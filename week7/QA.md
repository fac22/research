---
title: QA
tags: QA, Continuous Integration, Github Actions
author: @elenamarinaki
---

## QA
![](https://media.giphy.com/media/gG6OcTSRWaSis/giphy.gif)
*I am really sorry* 🤷‍♀️

---

## Continuous integration 👩‍💻
![](https://media.giphy.com/media/3o7buhsTerQAmHRztC/giphy.gif)

---

- **Continuous Integration**: People push to a Git repository and the code gets tested automatically.
- **Continuous Delivery**: The pushed code (ideally tested and bug-free) is then pushed into the server so it becomes live for users.

---

### Github actions 🙆‍♀️

- create a `.github` folder into an existing project with this structure ⬇️
```
- .github
  |- workflows
    |- action1.yml
    |- action2.yml
```

---

- let's create a very first action to test!
```
name: first-github-action
on: [push]
jobs:
  write-to-console:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'Hello world!!'
```

---

- going in the `Actions` tab in our github repo ➡️

![](https://i.imgur.com/3gQ5jYF.png)

---

- If you click into the workflow that ran, you’ll see a summary of what happened. This is where your job and action file name shows up.
![](https://i.imgur.com/eB0hnDa.gif)

---

### Github action events 🍋

---

Github Action Events determine when a workflow runs. The most basic event is a `push`, which means the workflow runs whenever something is pushed to the repository.

---

Other events are: *scheduled* events, *manual*, *webhook* and more...

---

### Github action jobs 🌽

---

Jobs let you define what to do. Each job begins with a “Job ID”. This ID is basically a slug you use. In this case, we have a write-to-console Job id.
```
jobs:
  write-to-console:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'Hello world!!'
  testing:
    # ...
  deploy:
    # ...
```

---

### Operating System 🐝

*Each* Job runs on a *specific operating system*. You can choose from Windows, Mac or Ubuntu (Linux) at the time of writing. These servers are called “runners” in Github Actions terminology.

```
jobs:
  write-to-console:
    runs-on: ubuntu-latest
```

---

## Defining what to do in each job 💭

---

`steps` let you define what to run in each job. 3 ways to define ↪
- `uses`
- `run`
- `name`

---

## `Uses` 🦊

↪ let you use Github Actions others have created.

```
steps:
  - uses: actions/checkout@v2
    with:
      repository: ''
      anotherArg: ''
```

---

The `-` signifies the step 🦶

---

### Using an existing action from the *Github Marketplace* - `Checkout`
This action checks-out your repository under $GITHUB_WORKSPACE , so your workflow can access it.

---

### What using `checkout@v2.4.0` looks like when successful 🎉
![](https://i.imgur.com/xaI8VO0.png)

---

### Post checkout
![](https://i.imgur.com/az72oSx.png)


---

## `Run` 🐇

↪  lets you create a custom label for the steps you want to run.

```
steps:
  # ...

  # Using Name + uses
  - name: Setup Node
    uses: actions/setup-node@v1

  # Using Name + Run
  - name: Say Hello
    run: echo 'Hello World!'
```

---

![](https://i.imgur.com/4rY3AuR.gif)

---

### ⚠️ Be careful with the syntax!

```
- name: Setup Node
    uses: actions/setup-node@v1
```
⬆️ this won't work! 😩 
The `uses:` ... is seen as a continuation of the previous value for name. But it's invalid, because **colons plus spaces aren't allowed in mapping values**.

---


```
- name: Setup Node
  uses: actions/setup-node@v1
```
⬆️ but this will!! 🤦‍♀️


![](https://media.giphy.com/media/xkh1NwYmXwv2o/giphy.gif)

---

### Incorrect syntax 🔥
will give you something like this ⬇️

![](https://i.imgur.com/2dg6uSz.png)

which you might endlessly chase down with no luck 🥳

---

## `Name` 🦄

↪ lets you create a custom label for the steps you want to run. Each `name` should come with either a set of commands — typically `with` or `run`.

---

Let's test a `uses` using an existing action `setup-node` with a `run` using an `echo` message.

```
- name: Setup Node.js environment
  uses: actions/setup-node@v2.4.1
- name: Say Hello
  run: echo 'I am tired!!! 😩'
```

---

![](https://i.imgur.com/vnIA5H8.gif)

---

### Last example (I promise 🙄)

![](https://media.giphy.com/media/13Syr1nwDffUcw/giphy.gif)

---

Closing stale issues with Github actions! ✨

```
steps:
  - name: Close Stale Issues
    uses: actions/stale@v4.0.0
```

---

![](https://i.imgur.com/uKR1C39.png)

---

That's it! 🤓 Feel free to ask any questions, there's tons more to research! 🙃
![](https://media.giphy.com/media/3oz8xIsloV7zOmt81G/giphy.gif)

---





