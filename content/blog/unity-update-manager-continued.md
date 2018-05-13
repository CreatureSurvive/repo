+++
title = "Unity Update Manager Continued"
date = 2016-09-10 
math = "false"
draft = "false"
+++

After receiving a good amount of feedback on my previous post \[Update Manager\](http://creaturecoding.com/update-manager/) I decided to write a followup post to fill in some of the information I left out in the original post.

One of the major details that I left out in the original post was the stats, and thats probably the most important one to include.

#### The Unity Method

I decided to profile the Unity `Update()` method to get a benchmark for comparison. For this test created two simple classes an `UpdateTester` class,

```csharp
public class UpdateTester : MonoBehaviour
{
	private void Update () {}
}
```

and an `UpdateSpawner` class for adding the UpdateTester to a gameobject during `Awake()`

```csharp
public class UpdateSpawner : MonoBehaviour
{
    [SerializeField]
    int amount = 10000;

    private void Awake()
    {
        for (int i = 0; i < amount; i++)
        {
            gameObject.AddComponent <UpdateTester>();
        }
    }
}
```

Before running the test I turned off Vsync in Edit>Project Setings>Quality. The test was ran within the editor with “deep profiling” enabled in the profiler.

For 10000 `Update()` calls it was averaging 8 - 9 ms per update loop and unity’s estimated FPS were at 78 - 84 fps.

![](https://creaturesurvive.github.io/repo/images/2016/09/Screenshot-at-Sep-09-20-12-06.png)

#### The UpdateManager Method(Array)

For this test all I had to change was the `UpdateTester` to use `BaseMonoBehaviour`. In this test I used the same UpdateManager from the previous [post](http://creaturecoding.com/update-manager/) using an array to store the `BaseMonoBehaviour` objects.

```csharp
public class UpdateTester : BaseMonoBehaviour
{
    public override void UpdateNormal (){}
}
```

In this test the results were drastically improved. For 10000 `Update()` calls it was averaging 1.5 - 2.3 ms per update loop and unity’s estimated FPS were at 240 - 250 fps.

![](https://creaturesurvive.github.io/repo/images/2016/09/Screenshot-at-Sep-09-20-23-17.png)

I did note that using the `UpdateManager` initial load times were longer due to the way the manager adds objects to the array. Im still testing methods of improving the way the arrays are handled to minimize allocation and garbage.

#### The UpdateManager Method(List)

In this test I had to modify the `UpdateManager` to use a generic List for storing the `BaseMonoBehaviour` objects.  
Due to the results I came up with during this test I am not going to post the changes I made to the `UpdateManager`.

The results in this test though still an improvement over unity’s `Update` method, they were much slower than using the arrays. For 10000 `Update()` calls it averaged 5.3 - 8.2 ms per update loop and unity’s estimated FPS were at 115 - 128 fps.

This is due to the overhead of List passing items from the list the object querying the list.

![](https://creaturesurvive.github.io/repo/images/2016/09/Screenshot-at-Sep-09-22-49-12.png)

#### The Comparison

| Unity Method | UpdateManager (Array) | UpdateManager (List) |
| ------------ | --------------------- | -------------------- |
| 8 - 9 ms     | 1.5 - 2.3 ms          | 5.3 - 8.2 ms         |
| 78 - 84 fps  | 240 - 250 fps         | 115 - 128 fps        |

As per the results using this update manager can greatly increase the speed of your update loop. However with its current state and how I implemented adding and removing objects from the manager I can’t recommend that you use it if you’re needing to instantiate lots of objects during gameplay as this could cause lag due to allocation and garbage collection. If your able to add and remove objects during loading then this implementation this should work fine for you.

I am still testing a few methods of optimizing this to minimize any overhead caused by adding and removing objects.