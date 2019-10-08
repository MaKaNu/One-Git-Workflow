# One-Git-Workflow
This is a brief description how I use (or should use) Git with Windows. It includes only the License and the Readme. This Intorduction uses GITHUB as example. If you are using any other plattform you maybe have to adjust some steps. All commands are executed with git as bash.

## Table of Contents

* [Complete Workflow](#mainheader1)
    * [First Step](#header1)
    * [Clone the Repository](#header2)
    * [Adding new Files](#header3)
    * [Commit your Files](#header4)
    * [Editing Files](#header5)
    * [Push Files](#header6)


## <a name="mainheader1"></a>Complete Workflow

### <a name="header1"></a>First Step
Maybe you have done this already, but every Work with git should start with a new Repository.


>**_NOTE:_** You may ask what is a repository or shortterm repo? A repository is a data container. Together with github the term is used for all data that is included in your Project that you clone.

If you are on the main page on Github ([https://github.com/](https://github.com/)) and logged in, you will find on the left side a repository list. You create a new repository by using the ([New](https://github.com/new)) Button.

On the following Page you give your new Repository a matching name and if u already now what your repository is about a short description. 

Then you a to decide wether you want a **public** or **private** repository.

I recommend to initialze a repository with a ```README```, a ```.gitignore``` and a ```LICENSE``` File. The ```LICENSE``` file  especially if you are using the public option. The ```.gitignore``` depends on the code language you want to use.

### <a name="header2"></a>Clone the Repository
After the creation of your repository you will find the ```Clone``` Button on the repository site. This Button opens a dropdown menu, which includes the url of the repository. In the case of this repository the url looks like this: [https://github.com/MaKaNu/One-Git-Workflow.git](https://github.com/MaKaNu/One-Git-Workflow.git) . Copy this Link and open the explorer. Move to a directory where you want to place your Repository on your Computer. I prefer to use a folder called _git_. Open the context menu by right-clicking the explorer and choose the option ```Git Bash Here```. This opens a git bash in the choosen folder. Now you can clone your repository:

```shell
git clone https://github.com/MaKaNu/One-Git-Workflow.git
```

The bash path should now look like this

```shell
user@computer MINGW64 /d/my-path-to-git/One-Git-Workflow (master)
```

### <a name="header3"></a>Adding new files
The best start of a new project beginns with the structure of the project. As example I describe a the structure of the game asteroids in the example folder of [pyglet](https://github.com/pyglet/pyglet):

- game
    - resources
        - ```asteroid.png```
        - ```bullet.png```
        - ```bullet.wav```
        - ```engine_flame.png```
        - ```player.png```
    - version1
        - game
            - ```__init__.py```
            - ```load.py```
            - ```resources.py```

        - asteroid.py

But often it is not possible to build the hole structure of a project from beginning. In both cases it is necessary for this workflow to add the empty files before editing them. To do this we check the status of the repository:

```shell
git status
```

The result should look like this:

```shell
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        new_file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

>**_NOTE:_** if it looks like this, you have probalby edited some files:
```shell
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        new_file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

The Goal is to have only ```untracked files``` or  ```Changes not staged for commit``` at one time, not both together.

Now we start tracking all new files with one command:

```shell
git add --all
```

### <a name="header4"></a>Commit your Files

In this workflow the commit should include two messages. The first should be a prominent Title. For the track commit for new files the message could be "Initiate New Files". The second message should describe more details, like "tracked files: new_file.txt". The command looks like this:

```shell
git commit -m "Initiate New Files" -m "tracked files: new_file.txt"
```

### <a name="header5"></a>Editing Files
After you have commited your empty files, so they are tracked now, you can start editing them. Before adding them you should check status once again, it now should look like this as mentioned [above](#header4):

```shell
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

You use the ```add```command again but with a different Option:

```shell
git add -p
```

The option ```-p``` stands for patch and allows you to go through your code and review it before adding. It divides every change in patches and you have to choose if you want to add it or not. Every patch ends with a list of possible command:

```shell
Stage this hunk [y,n,q,a,d,e,?]?
```

At the moment we only need ```y,n,q```. The command ```y``` stages the patch and ```n``` skips the patch. You can use ```q``` if you want to break the add process. 

### <a name="header6"></a>Push Files

The last step is to take your files online:

```shell
git push
```

### <a name="header7"></a>Pull Files

If you want to work on a different Computer you need to pull your files from your repository. If it is the first time you work on the new computer you simply can use [clone](#header2). After the initial clone you have to use the command ```pull```.

```shell
git pull
```
This simply downloads the newest version from your online repository, which you have pushed before from a different system.

>**_NOTE_**: In this Workflow we didn't talk about branches. If you already familar about branches take care about in which branch you are working







