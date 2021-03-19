---
title: "Get Started: Hello, Flyte!"
---

The goal of this tutorial is to modify an existing example (hello world) to take the name of the person to green as an argument.

## Prerequisites


:::tip 

Ensure that you have git installed.

:::

## Steps

* First install the python Flytekit SDK and clone the flytesnacks repo:

```
pip install --pre flytekit
git clone git@github.com:flyteorg/flytesnacks.git flytesnacks
cd flytesnacks
```

* The repo comes with some useful Make targets to make your experimentation workflow easier. Run make help to get the supported commands. Let’s start a sandbox cluster:

```
make start
```

* Take a minute to explore Flyte Console through the provided URL.

![Docusaurus logo](/img/hello-world.gif)

* Open `hello_world.py` in your favorite editor.

```
cookbook/core/basic/hello_world.py
```

* Add `name: str` as an argument to both `my_wf` and `say_hello` functions. Then update the body of `say_hello` to consume that argument.

```
@task
def say_hello(name: str) -> str:
    return f"hello world, {name}"
```

```
@workflow
def my_wf(name: str) -> str:
    res = say_hello(name=name)
    return res
```

* Update the simple test at the bottom of the file to pass in a name. E.g.

```
print(f"Running my_wf(name='adam') {my_wf(name='adam')}")
```

* When you run this file locally, it should output hello world, adam. Run this command in your terminal:

```
python cookbook/core/basic/hello_world.py
```

Congratulations! You have just ran your first workflow. Let’s now run it on the sandbox cluster you deployed earlier.

* Run:

```
REGISTRY=ghcr.io/flyteorg make fast_register
```

* Visit the [console](http://localhost:30081/console/projects/flytesnacks/domains/development/workflows/core.basic.hello_world.my_wf), click launch, and enter your name as the input.

* Give it a minute and one it’s done, check out “Inputs/Outputs” on the top right corner to see your greeting updated.

