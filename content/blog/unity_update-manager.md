+++
date = "2016-09-04"
title = "Unity Update Manager"
math = "false"
draft = "false"
+++


### What is an update manager?

An update manager is a class that holds a reference to all of your `MonoBehaviour`'s and executes all of their `Update()` methods each frame.

### What is the benefit of an update manager?

An update manager is very useful when you have a large amount of `Monobehaviour`'s using the `Update()` method.

### Whats wrong with using lots of Updates?

`MonoBehaviour`'s handle all of unity's _'Magic Methods'_(I'll explain these in a minute) and though typically you wouldn't need to worry about how unity handles these methods, when you end up with a lot of them it can start bogging down your performance.

Take this for example, we have a scene in which we need to spawn 1000 cubes and move them around. Lets create new scene and add a cube in it.  
now lets create a new script to update the position of the cube

```csharp
using UnityEngine;

public class RandomCubeMover : MonoBehaviour
{
    float speed = 10.0f;
    Vector3 vel;
    void Update()
    {
        vel = Random.onUnitSphere * speed;
        transform.Translate (vel* Time.deltaTime);
    }
}
```

Now lets add this to script to the cube in our scene.

You can hit play and watch your cube moving around like this.  
![gif](https://creaturesurvive.github.io/repo/images/2016/09/Sep-04-2016-20-07-08-CubeMovement.gif)

Lets make this cube into a prefab by dragging it from the hierarchy into our project browser. Now lets make a spawn manager class to spawn out 1000 cubes when we hit play

```csharp
using UnityEngine;

public class SpawnManager : MonoBehaviour
{
    [SerializeField]int amountToSpawn = 1000;
    [SerializeField]GameObject cubePrefab;

    int spawnAmount;

    void Start()
    {
        while (spawnAmount < amountToSpawn)
        {
            GameObject cube;
            cube = Instantiate (cubePrefab, transform.position, Quaternion.identity) as GameObject;
            cube.transform.SetParent (transform);
            spawnAmount++;
        }
    }
}
```

Create an empty gameobject in your scene and call it 'SpawnManager'  
Add this script to the object, and drag the 'Cube' prefab from the project browser into the 'cubePrefab' field. Now when you hit play 1000 cubes will spawn and dance around.

![](https://creaturesurvive.github.io/repo/images/2016/09/Sep-05-2016-00-42-07-1000-Cube-Movement.gif)

If you check the stats you can see this has already brought our performance way down.

### How does calling update effect performance?

Back to the term _'Magic Methods'_, _'Magic Methods'_ are all the methods inherited from `MonoBehaviour` such as `Awake()`, `Start()`, `Update()`, `FixedUpdate()`, etc... When a `MonoBehaviour` is accessed for the first time, it is then scanned by the [Common Language Runtime (CLR)](https://msdn.microsoft.com/en-us/library/8bs2ecf4(v=vs.110).aspx) for any _'Magic Methods'_ it may have in it. When the `MonoBehaviour` is scanned, all the _'Magic Methods'_ within it are then added to lists i.e. a list of `Update()` methods, a list of `Start()` methods, etc. Then when Unity calls these functions it simply iterates through the list of methods.

All of our C# scripts that we create inside Unity are compiled into _Managed Code_, managed code is code that is read and interpreted by the CLR. whereas Unity is made up of C++ that is compiled into _Native Code_, native code is code that is read and interpreted directly by the computer making it really fast.

So here is the problem with this, Unity handles executing all of the magic methods from within the engine meaning its handled in _Native Code_, however the methods it is executing are contained in the _Managed Code_. Every time a method is executed from _native_ to _managed_ it generates overhead. So if we have 1000 Updated being called each frame thats taking that overhead and multiplying it by 1000, this really slows things down. Heres where the Update Manager comes in.

### How does the update manager increases performance.

An Update Manager works the exact same way as unity handles its _'Magic Methods'_, it simply has a list of all the methods and executes them as needed. However there is one key difference, **It's all handled in Managed Code**, so instead of suffering the same overhead as the unity implementation on a per call basis, it only generates overhead once.

### Creating the update manager

Now that we understand the issue with unity's implementation we can effectively come up with a solution.

First we need a way to keep track of all the classes that contain _'Magic Methods'_. We could do this by creating a list of all our `MonoBehaviour`'s but that wouldn't allow us to control method execution. Instead lets extend `MonoBehaviour` by creating a new class that inherits from `MonoBehaviour` and add some virtual methods we can overload later.

```csharp
public abstract class BaseMonoBehaviour : MonoBehaviour
{       
    public virtual void UpdateNormal() {}
        
    public virtual void UpdateFixed() {}

    public virtual void UpdateLate() {}
}
```

​    

We want this class to be abstract because we are going to be inheriting from it but we won't always need all the methods within it also it allows us control over how the interface methods are called.

Now all our `MonoBehaviour` classes instead of inheriting from `MonoBehaviour` we'll inherit from `BaseMonoBehavoir` and instead of using `void Update()` we will use `public override void UpdateNormal()`.

Now we need the manager its self this will be the class responsible for storing a reference to all our `BaseMonoBehaviour`'s and executing methods. We will also need a way of accessing methods within it easily so that each `BaseMonoBehaviour` doesn't need to hold a reference to it in order to be added to the manager, for this we can just create a static instance of the Manager in its constructor so that the first time its accessed a static instance will me stored for easy access [(singleton)](https://msdn.microsoft.com/en-us/library/ff650316.aspx)

```csharp
using UnityEngine;

public class UpdateManager : MonoBehaviour
{
    private int behaviourCount;
    private BaseMonoBehaviour[] behaviors;

    private static UpdateManager instance;

    public UpdateManager()
    {
        instance = this;
    }
}
```

Now lets add some functionality to this. We'll need methods for adding and removing behaviors from the manager so lets start with that by creating some static methods for adding and removing items.

```csharp
public static void AddBehaviour(BaseMonoBehaviour behaviour)
{
    if (instance.behaviours == null)
    {
        behaviours = new BaseMonoBehaviour[1];
    }
    else
    {
        System.Array.Resize(ref instance.behaviours, instance.behaviours.Length + 1);
    }
    instance.behaviours[behaviours.Length - 1] = behaviour;
    instance.behaviourCount = behaviours.Length;
}

public static void RemoveBehaviour(BaseMonoBehaviour behaviour)
{
    int addAtIndex;
    BaseMonoBehaviour[] tempBehavioursArray = new BaseMonoBehaviour[behaviours.Length - 1];
    for (int i = 0; i < instance.behaviours.Length; i++)
    {
        if (instance.behaviours[i] == null)
        {
            continue;
        }
        else if (instance.behaviours[i] == behaviour)
        {
            continue;
        }
        tempArray[addAtIndex] = behaviours[i];
        addAtIndex++;
    }

    instance.behaviours = new BaseMonoBehaviour[tempArray.Length];
    
    for (int i = 0; i < tempArray.Length; i++)
    {
        instance.behaviours[i] = tempArray[i];
    }
    instance.behaviourCount = instance.behaviours.Length.
}
```

Now that we have the methods for adding and removing behaviours from the manager, we need to create some methods for calling `UpdateNormal()`, `UpdateFixed()`, and `UpdateLate()` within our `BaseMonoBehaviour`'s.  
These methods will be really simple all they need to do is iterate through the array of behaviours within the manager and execute these methods. Notice that we made our Update Manager a regular `MonoBehaviour` thats because we are going to use `Update()`, `LateUpdate()`, and `FixedUpdate()` as regular _'Magic Methods'_ to handle calling our `BaseMonobehaviour` methods.

```csharp
private void Update()
{
    if (behaviourCount > 0)
    {
        for (var i = 0; i < behaviours.Length; i++)
        {
            if (behaviours[i] == null || !behaviours[i].isActiveAndEnabled)
            {
                continue;
            }
            behaviours[i].UpdateNormal();
        }
    }
}

private void FixedUpdate()
{
    if (behaviourCount > 0)
    {
        for (var i = 0; i < behaviours.Length; i++)
        {
            if (behaviours[i] == null || !behaviours[i].isActiveAndEnabled)
            {
                continue;
            }
            behaviours[i].UpdateFixed();
        }
    }
}

private void LateUpdate()
{
    if (behaviourCount > 0)
    {
        for (var i = 0; i < behaviours.Length; i++)
        {
            if (behaviours[i] == null || !behaviours[i].isActiveAndEnabled)
            {
                continue;
            }
            behaviours[i].UpdateLate();
        }
    }
}
```

Now that we have all our update manager set up lets look into adding our `BaseMonoBehaviour`'s to it automatically. Within the any class we implement `BaseMonoBehaviour` we could simply add the behaviour to the `UpdateManager`in the `Awake()` method but it would be great if we could handle this without having to do it manually. So instead lets handle this in the `Awake()` method within the `BaseMonoBehaviour` class. We know that the Awake method will be called in this class even if we don't implement it in our behaviour. just to ensure that we don't call this method from outside the `BaseMonoBehaviour` class its self lets make this method protected. So back in the `BaseMonoBehaviour` class lets add this method.

```csharp
protected virtual void Awake()
{
    UpdateManager.AddBehaviour(this);
}
```

### Using the update manager.

Using the update manager is almost the same as using unity built in method. Now in your classes instead of calling `void Update()` you do this `public override void UpdateNormal()`

Lets go back to our original example and update it to use our `UpdateManager`. All we need to do is inherit from `BaseMonoBehaviour` instead of `MonoBehaviour` and change our `Update()` method.

```csharp
using UnityEngine;

public class RandomCubeMover : BaseMonoBehaviour
{
    float speed = 10.0f;
    Vector3 vel;
    public override void UpdateNormal ()
    {
        vel = Random.onUnitSphere * speed;
        transform.Translate (vel* Time.deltaTime);
    }
}
```

If you need do use Awake within your class the instead of calling `void Awake()` use `protected override void Awake()` though unlike with the `UpdateNormal` method you also need to call `base.Awake` this will execute the method within the base class ensuring this behaviour gets added to the `UpdateManager`

so your methods should look like this

```csharp
protected override void Awake()
{
    base.Awake();
    //Your code goes here
}

public override void UpdateNormal()
{
    //Your code goes here
}

public override void UpdateFixed()
{
    //Your code goes here
}

public override void UpdateLate()
{
    //Your code goes here
}
```

If anyone is interested in implementing execution order into the `UpdateManager` just let me know and I can write another post adding this functionality.

This was my first blog post ever, I hope it was helpful.