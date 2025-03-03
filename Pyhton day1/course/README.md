# Advanced-programming M2 2024-25  <!-- omit in toc -->

This is the repository for the advance programming first semester class of M2 at amU 2024-25

- [1. Prelude](#1-prelude)
  - [1.1. What is coding?](#11-what-is-coding)
  - [1.2. What is a programming language?](#12-what-is-a-programming-language)
  - [1.3. What computers are good and not so good at](#13-what-computers-are-good-and-not-so-good-at)
  - [1.4. Prerequisites](#14-prerequisites)
  - [1.5. Goal of this course](#15-goal-of-this-course)
- [2. But first what will be our biological question](#2-but-first-what-will-be-our-biological-question)
  - [2.1. Flocks and Schools](#21-flocks-and-schools)
  - [2.2. Emergent behaviours, complex systems and collective behaviour](#22-emergent-behaviours-complex-systems-and-collective-behaviour)
  - [2.3. Implementing a complex system using simple rules](#23-implementing-a-complex-system-using-simple-rules)
- [3. What will be our support?](#3-what-will-be-our-support)
- [4. Setting up a decent working environment](#4-setting-up-a-decent-working-environment)
  - [4.1. Why should I use an IDE?](#41-why-should-i-use-an-ide)
  - [4.2. What is a virtual environment?](#42-what-is-a-virtual-environment)
  - [4.3. Why should I use a virtual environment?](#43-why-should-i-use-a-virtual-environment)
  - [4.4. How to create a virtual environment?](#44-how-to-create-a-virtual-environment)
  - [4.5. DO NOT INSTALL THINGS IN THE BASE ENVIRONMENT](#45-do-not-install-things-in-the-base-environment)
  - [4.6. Why should I use versioning (git)?](#46-why-should-i-use-versioning-git)
  - [4.7. Live GitHub tutorial](#47-live-github-tutorial)
- [5. A quick test](#5-a-quick-test)
- [6. Back to basics of coding](#6-back-to-basics-of-coding)
  - [6.1. Variables](#61-variables)
  - [6.2. Data structures](#62-data-structures)
  - [6.3. Conditional statements \& loops](#63-conditional-statements--loops)
  - [6.4. Functions](#64-functions)
- [7. Classes](#7-classes)
- [8. Packaging your code](#8-packaging-your-code)
- [9. Interaction between multiple boids](#9-interaction-between-multiple-boids)
- [10. Visualising the boids](#10-visualising-the-boids)

## 1. Prelude

A "quick" prelude before starting

### 1.1. What is coding?

Coding is giving a set of instructions to a computer for it to do a task.
The tasks can be as trivial as:

```pseudo
Give the result of 1 + 0
```

or, slightly more complex:

```pseudo
If the key 'a' from the keyboard is stroke, display the letter 'a' on the screen
```

or quite complex:

```pseudo
Prove the 4-colour theorem
```

(see [Computer-assisted proofs](https://en.wikipedia.org/wiki/Computer-assisted_proof))

### 1.2. What is a programming language?

To communicate and give instructions to a computer, it is necessary to deliver the said instructions in a language that the computer can indeed understand, this is the language.
The units of a computer that receive and perform these instructions are either the Central Processing Unit (CPU) or the Graphics Processing Unit (GPU).
For the remainder of this class we will only work with CPUs and therefore we will __not__ discuss GPUs.

What defines a language is the CPU architecture ([x86](https://en.wikipedia.org/wiki/X86) or [ARM](https://en.wikipedia.org/wiki/ARM_architecture_family) for example).
The CPU language (called machine code) is (almost always) a binary code.
In other words it is made of 0s and 1s that combined produces instructions for the CPU to process.
This language, which cannot be "easily" read by mere mortals like us.
This is why programming languages exist (simplifying a bit here).
A programming language is basically a more readable way to write instructions to a CPU.
A compiler or interpreter then transforms the said language into specific Machine code that the CPU can understand.

There is an extremely large number of programming languages (635 listed on this [wikipedia page](https://en.wikipedia.org/wiki/List_of_programming_languages)). For example C++, Visual Basic, Java, R, Go, ...

### 1.3. What computers are good and not so good at

It is also important to understand what computers are good at and not so good at.
Computers have strengths and weaknesses. They are especially good at:

- performing basic operations: additions, multiplications, ...
- accessing their short and long term memory

For example, current common processors are working at $2.5GHz\simeq 2.5\times 10^9$ actions per second, meaning that if you would perform 1 action every second it would take you about 800 years to perform as many actions as a computer is doing in one second.

Computers are also good at storing information and accessing it.
Computers can store about 1TB of data in "slow-to-access" memory and about 32GB of data in fast access memory (RAM).
To put that in context, 1 hour of Netflix movie in HD weighs about 3GB, so 3TB is 1000 hours of Netflix movie which is about 42 days of film.

On top of that, computers can access the data in memory quickly.
Computers can read from 80 to 160 MB per second, Solid State Drives (SSD) can read at a speed of 550MB per seconds.
In other words, a computer can learn "by heart" the whole _A song of Ice and Fire_ series in about a second.
Finally, Random Access Memory (RAM), which is the memory that directly exchanges information with the CPUs read at a speed of about 1500MHz.
(Note that for read/write intensive processes it can become a limiting factor for the overall processing speed)

On the flip side, computers are not good at everything. For example, they are bad at:

- Pattern recognition
- Being creative (building hypotheses, making jokes, writing good novels, ...)
- Anything that doesn’t have pre-existing data for

Though, these limitations have been pushed back significantly recently thanks to the artificial intelligence and deep learning revolution.
One very notable, recent example: [AlphaGO](https://www.deepmind.com/research/highlighted-research/alphago), the first program that beat a human at the GO game. For the first time, computers could have intuition-like behaviours that are better than humans and even that we cannot understand.

### 1.4. Prerequisites

1. An IDE (Integrated Development Environment), I personally suggest [Visual Studio Code](https://code.visualstudio.com/) but feel free to use any other (ie [pycharm](https://www.jetbrains.com/pycharm/), [spyder](https://www.spyder-ide.org/), [emacs](https://www.gnu.org/software/emacs/)). Note that I might not be able to help you as easily with other IDEs
2. An environment manager I __strongly__ suggest [miniforge](https://github.com/conda-forge/miniforge). I __VERY STRONGLY__ advise __AGAINST__ anaconda (we can discuss why)
3. Python installed (it should already be the case)
4. Few libraries will be useful (THAT YOU SHOULD INSTALL IN A DEDICATED ENVIRONMENT, see below):
   1. [`numpy`](https://numpy.org)
   2. [`scipy`](https://scipy.org)
   3. [`matplotlib`](https://matplotlib.org)
   4. [`pygame`](https://pygame.org)

As an __important__ note, please read what the installers are asking you

### 1.5. Goal of this course

This class is a more in depth introduction to programming and software engineering.
At the end of this course I hope that you will have learnt the following:

1. How to (rudimentarily) use Git through GitHub
2. How to decently write code that can be used by other users __and__ developers. (PEP, docstring, formatting, black, ruff, ...)
3. That there are often (if not always) multiple ways to implement a given problem, some ways are better than others, some ways are easier than others.
4. How to make _pip installable_ and therefore easier to disseminate a project.

## 2. But first what will be our biological question

### 2.1. Flocks and Schools

Birds and fish often move as flocks or schools.
Flock and school patterns are quite unique, some could even find them beautiful.
When observing them, one could assume that to achieve such coordinated behaviour one of the two following rules is true.
Either there would be one or multiple leaders that would drive and stir the other individuals.
Or, all individuals should know at all times the position and intent of every other individual and could adapt, in a collective manner, to that.

In these two hypotheses, there is the assumption that at least a small number of individuals have a global knowledge of the current situation, at all times.

### 2.2. Emergent behaviours, complex systems and collective behaviour

Another hypothesis is that each individual only has a knowledge of its surroundings and that a few simple local rules create such large, beautiful patterns.
Basically, this observed complex collective behaviour __emerges__ from simple and local rules.
These kinds of behaviours are observed in many biological systems and populations, in fish schools, bird flocks but also ants, life itself and so on and so forth.

### 2.3. Implementing a complex system using simple rules

In this class we will show that only local information can produce flocks and schools behaviours
by implementing our version of [boids](https://en.wikipedia.org/wiki/Boids).

From [Wikipedia](https://en.wikipedia.org/wiki/Boids):
> Boids is an artificial life program, developed by Craig Reynolds in 1986, which simulates the flocking behaviour of birds, and related group motion.
> His paper on this topic was published in 1987 in the proceedings of the ACM SIGGRAPH conference.(1)
> The name "boid" corresponds to a shortened version of "bird-oid object", which refers to a bird-like object.(2)
> Reynolds' boid model is one example of a larger general concept, for which many other variations have been developed since.
> The closely related work of Ichiro Aoki is noteworthy because it was published in 1982 — five years before Reynolds' boids paper.(3)
>
> (1): Reynolds, Craig (1987). "Flocks, herds and schools: A distributed behavioural model". Proceedings of the 14th annual conference on Computer graphics and interactive techniques. Association for Computing Machinery. pp. 25–34.
>
> (2): Banks, Alec; Vincent, Jonathan; Anyakoha, Chukwudi (July 2007). "A review of particle swarm optimization. Part I: background and development". Natural Computing. 6 (4): 467–484.
>
> (3): Aoki, Ichiro (August 25, 1982). "A Simulation Study on the Schooling Mechanism in Fish". Nippon Suisan Gakkaishi (Japanese Fisheries Academic Journal). 48 (8): 1081–1088.

The only rules boids need to behave like a flock are the following:

__Rule 1__: __Coherence__: Boids try to fly towards the centre of mass of their neighbourhood

__Rule 2__: __Separation__: Boids try to stay a reasonable amount away from each other to avoid collision

__Rule 3__: __Alignment__: Boids try to match the velocity of their nearby boids.

## 3. What will be our support?

In this class we will code in Python because:

1. It is free and open source
2. It is the most used languages, source: [TIOBE-index](https://www.tiobe.com/tiobe-index/)
3. It is one of the most used languages in data science, source: Trust.me.I.know.someone.gov
4. It is one of the most used languages in deep learning, source: Trust.me.I.know.someone.gov
5. It is the language I am the most familiar with (!)
6. __It is free and open source__

## 4. Setting up a decent working environment

A good working environment is the recipe for a good, useful code.
For this class you will have to use different developing tools.
Some will be mandatory, others will be optional (though highly recommended).

Mandatory tools:

- [GitHub](https://github.com/)
- [miniforge](https://github.com/conda-forge/miniforge) (or another virtual environment manager)
- [pip](https://pypi.org/)
- [black](https://github.com/psf/black)
- [ruff](https://docs.astral.sh/ruff/)

Optional tool:

- [Visual Studio Code](https://code.visualstudio.com/) (or another IDE)

### 4.1. Why should I use an IDE?

When starting to develop larger programs, having an overview of your folder structure is important.
Moreover IDEs most of the time give you access to ease of life features:

- autocompletion
- good highlighting of the code
- debugging tools
- comes with its own terminal (very useful on Windows which does not have a decent native terminal)
- seamless remote access to external machines
- integration of GitHub
- [...]

### 4.2. What is a virtual environment?

From the [CS guide of Princeton University](https://csguide.cs.princeton.edu/software/virtualenv):

> A Python virtual environment (venv) is simply a directory with a particular file structure.
> It has a bin subdirectory that includes links to a Python interpreter as well as subdirectories that hold packages installed in the specific venv.
> By invoking the Python interpreter using the path to the venv's bin subdirectory, the Python interpreter “knows” to use the associated packages within the venv (as opposed to any packages installed alongside the actual location of the Python interpreter).
> It is in this sense that venvs are “virtual”—they are not virtual in the sense of, say, a virtual machine.

### 4.3. Why should I use a virtual environment?

> Virtual environments let you have a stable, reproducible, and portable environment.
> You are in control of which package versions are installed and when they are upgraded.
> You can have as many venvs as you want.

### 4.4. How to create a virtual environment?

Note that there are many different tools to manage venvs:

- `conda`/`mamba`
- `venv`
- `Poetry`
- `Pipenv`
- [...]

The choice of using `conda`/`mamba` is really personal, feel free to try others if you'd like to.

I assume that you already have installed `miniforge`.
You can then open the terminal of your choice.
Then you can create a venv the following way:

```shell
mamba create -n my-venv
```

or (if you have `conda` installed instead of `mamba`)

```shell
conda create -n my-venv
```

You can then activate your environment the following way:

```shell
mamba activate my-venv
```

or

```shell
conda activate my-venv
```

Once activated you can install whatever you want to in your environment but remember that when created as proposed above, the environment is empty, it does not even have Python installed.

You can install Python the following way:

```shell
mamba install python=3.10 # to get version 3.10 of python for example
```

if you remove the `=3.10` you will install the latest stable release of Python, it might be problematic in some cases.

To automatically install Python 3.10 (or any other library or Python version for that matter) when creating your environment, you can use the following line:

```shell
mamba create -n my-env python=3.10
```

### 4.5. DO NOT INSTALL THINGS IN THE BASE ENVIRONMENT

JUST DO NOT DO IT. IF YOU DO, IT WILL BE THE SOURCE OF ALL SORTS OF BAD HEADACHES!

### 4.6. Why should I use versioning (git)?

Because it allows you to:

- Easily share your code
- Go back in time
- Safely develop features
- Any decent company will use code versioning so you better know about it

### 4.7. Live GitHub tutorial

...

## 5. A quick test

Before starting for real, we will perform a quick series of exercises for me to have an idea of the global level of the class.

## 6. Back to basics of coding

### 6.1. Variables

see [1.Variables.ipynb](notebooks/1.Variables.ipynb)

- What is a variable?
- What are the different types of variables?
  - `Integer`
  - `Float`
  - `String`
- Difference between compiled and interpreted?

### 6.2. Data structures

see [2.Data-Structures.ipynb](notebooks/2.Data-Structures.ipynb)

- What are data structures?
- What are they good for?
- Common data structures in Python:
  - `List`
  - `Tuple`
  - `Dictionary`
  - `Set`
  - `np.ndarray`
  - [...]

### 6.3. Conditional statements & loops

see [3.Conditional-Statements-Loops.ipynb](notebooks/3.Conditional-Statements-Loops.ipynb)

- What are conditional statements?
- Bread and butter of coding
- Common conditional statements:
  - `if`
  - `else`
  - `elif`
- What are loops?
- Common loops:
  - `for`
  - `while`

### 6.4. Functions

see [4.Functions.ipynb](notebooks/4.Functions.ipynb)

- What is a function?
  - name
  - arguments
  - return value
- What is it good for?

## 7. Classes

see:

- [5.Classes.ipynb](notebooks/5.Classes.ipynb)
- [6.Class-initialisation.ipynb](notebooks/6.Class-initialisation.ipynb)
- [7.Boids.ipynb](notebooks/7.Boids.ipynb)

## 8. Packaging your code

Now that your are really good at writing classes, we can quickly talk about how they can be useful and how to make them accessible globally.

We will look together at your first "assignment" [there](https://classroom.github.com/a/ZiZbYGxv)

## 9. Interaction between multiple boids

see [8.Multiple-Boids.ipynb](notebooks/8.Multiple-Boids.ipynb)

## 10. Visualising the boids

see [9.Visualising-Boids.ipynb](notebooks/9.Visualising-Boids.ipynb)

An example for argparse: https://gist.github.com/leoguignard/ffa4bf5a239d463f4a4082bb3176c3fc
