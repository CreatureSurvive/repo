---
title: "Cydia Repo Update Cli"
date: 2018-06-01T16:24:27-05:00
draft: false
math: false
---

## Cydia Repo Update CLI

------

​	I decided to make a script for updating my Cydia repo in a less cumbersome way. It used to be that I would have to update my bash script every time I wanted to add/update a package on my repo. This got to be tedious and all around unnecessary. In addition to my workflow obviously needing some improvement, I also saw it as an opportunity to brush up on my near non-existent bash skills.

Some goals I had in mind while making this:

- No need to update my bash script.
- Optionally clean the package directory.
- Commit the changes when complete.
- Pass project directory as a parameter
- Display errors and help messages 


### Usage:

```language-bash
Usage: ./update-repo.sh -m --commit-message

  -m, --commit-message      The git commit message
  -g, --git-commit          If passed, then commit changes
  -p, --project-directory   the theos project directory
  -c, --clean-debs          remove old debs i.e. no downgrade option
  -h, -help                 display this help message

Example: ./update-repo.sh --commit-message 'rebuild packages' --project-directory my_tweak

```


### Code:

{{< gist CreatureSurvive ac6cda3ba164449553693bee6acaaae6 >}}

Hopefully others will find this as useful as I have.
