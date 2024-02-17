### Git 
- Version control system.
- A command line tool which is used to keep track of change made to the code.
- Allowing us to keep track of changes we make to our code by saving snapshots of our code at a given point in time.

![Changing File](https://cs50.harvard.edu/web/2020/notes/1/images/change_file.png)

- Allowing us to easily synchronize code between different people working on the same project by allowing multiple people to pull information from and push information to a repository stored on the web.

![Multiple Users](https://cs50.harvard.edu/web/2020/notes/1/images/mult_users.png)

- Allowing us to make changes to and test out code ==on a different branch ==without altering our main code base, and then merging the two together.
- Allowing us to ==revert back== to earlier versions of our code if we realize we’ve made a mistake.
### Push
- Making changes and then pushing the code to the server
### Pull
- Pulling code from the server and then making changes
### GitHub
- GitHub is a website that is used to store Git repositories on the web.

### Commands
- ##### git clone
```bash
git clone <url>
```
- In your terminal, run `git clone <repository url>`. This will download the repository to your computer. If you didn’t create a README, you will get the warning: `You appear to have cloned into an empty repository.` This is normal, and there’s no need to worry about it.

==Note: git does not keep track of any changes unless we commit those changes.==
- ##### git add
```shell
git add <filename>
```
- git add used to add the files of which we want to take a snapshot of.
- these are the files of which git commit will take snapshot of.

- ##### git commit
```shell
git commit -m "message"
```
- the -m is used to specify that we want to provide a message
```shell
git commit -am "message"
```
- the -am is used to specify the we want to add all those files that have been changes and also provide a commit message.
- ##### git status
```shell
git status
```
- git status tells us the current state of our local git repository.

- ##### git pull
```shell
git pull
```

### Merge Conflicts
- A merge conflict occurs when two people attempt to change a file in ways that conflict with each other.
- This will typically occur when you either `git push` or `git pull`. When this happens, Git will automatically change the file into a format that clearly outlines what the conflict is. Here’s an example where the same line was added in two different ways:

```
a = 1
<<<<< HEAD
b = 2
=====
b = 3
>>>>> 56782736387980937883
c = 3
d = 4
e = 5
```

- In the above example, you added the line `b = 2` and another person wrote `b = 3`, and now we must choose one of those to keep. The long number is ==a _hash_== that represents the commit that is conflicting with your edits. Many text editors will also provide highlighting and simple options such as “accept current” or “accept incoming” that save you the time of deleting the added lines above.
- Another potentially useful git command is `git log`, which gives you a history of all of your commits on that repository.

![Git Log](https://cs50.harvard.edu/web/2020/notes/1/images/git_log.png)

- #### git log
- gets the list of the commits that have been made

- ##### git reset
- Potentially even more helpful, if you realize that you’ve made a mistake, you can revert back to a previous commit using the command `git reset` in one of two ways:
    - `git reset --hard <commit>` reverts your code to exactly how it was after the specified commit. To specify the commit, use the commit hash associated with a commit which can be found using `git log` as shown above.
    - `git reset --hard origin/master` reverts your code to the version currently stored online on Git-hub.

### Branching
- After you’ve been working on a project for some time, you may decide that you want to add an additional feature. At the moment, we may just commit changes to this new feature as shown in the graphic below

![No Branch](https://cs50.harvard.edu/web/2020/notes/1/images/no_branch.png)

But this could become problematic if we then discover a bug in our original code, and want to revert back without changing the new feature. This is where branching can become really useful.

- Branching is a method of moving into a new direction when creating a new feature, and only combining this new feature with the main part of your code, or the main branch, once you’re finished. This workflow will look more like the below graphic:

![Branch](https://cs50.harvard.edu/web/2020/notes/1/images/branch.png)

- the current working branch is pointed by a HEAD

- ##### git branch
```shell 
git branch
```
- tells use the current working branch

- ##### git checkout
```shell
git checkout -b <newbrachname>
```
- creates the new branch and also changes the current working branch
```shell
git checkout <branchname>
```
- this is used to change the current working branch

- ##### git merge
```shell
git merge <otherbranchname>
```
- this command is used to merge the current branch for example main with the name of branch we provide.

#### Forking
- As a GitHub user, you have the ability to _fork_ any repository that you have access to, which creates a copy of the repository that you are the owner of. We do this by clicking the “Fork” button in the top-right.