---
title: The Testable Documentation Manifesto
layout: post
published_date: 2017-09-24 11:00:00 +0100
---

One of the problems with tech documentation (api, installation instructions etc) is that they get stale. APIs change, software and plugins alter their interface and commands, and websites go away.

To solve this, I propose we write our documentation in a way that can be executed, or verified.

Luckily, I wrote [`blaze`](https://gist.github.com/0atman/5ea526a3ae26409da50dd7697eb700e8) to execute codeblocks inside of markdown, which means that with a little help from a few common unix tools, we can solve this problem.


# Testable Software Installation Example


```shell

set -e
pip install badpackage_123183183
```

The output of executing the very file you are reading now is:

> $ ./README.md
>
> Collecting badpackage_123183183
>
>   Could not find a version that satisfies the requirement badpackage_123183183 (from versions: )
> No matching distribution found for badpackage_123183183

You now can execute your readme instructions as part of your build process (perhaps with a little setup beforehand, such as running it inside a container), and the exit code (in this case 1) will allow you to fail the build if the instructions are out of date.

You can get the [gist](https://gist.github.com/0atman/242cf9d6d99f2fbeb182a090213cf74a) of it here.

### Related
 - [blaze](https://github.com/0atman/blaze)  is lit. It allows language-agnostic literate-style programming
