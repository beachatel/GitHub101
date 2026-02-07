<h1> How to use Git and GitHub </h1> 
<h2> Why do I keep yapping about GitHub??</h2>

<h3> GitHub is great for 4 reasons: </h3>

1. You can store huge amounts of code on the cloud, for free. This allows you to access your code from any machine in the world with an internet connection. GitHub also preserves important folder structures that other cloud services do not. <br>

2. You can track changes in your code, this allows you to version control. Meaning you can revert back to a specific point in your code when something worked/didn't work. This is especially great when you have lots of different itterations of something and you might want to document the process. <br>

3. Collaboration. For large projects with multiple people GitHub is the perfect way to collab on code. You can make requests to change something, submit issues and coordinate across the project.<br>

4. Open Source. There are more than 28 million public repositories on GitHub that allow you to view, download and edit their contents. Think of all the learning :nerd_face:.

 <h2> What GitHub is <ins>NOT</ins> for</h2>

GitHub is not for storing media. It is not a replacement for cloud storage like Google Drive or OneDrive. It will break if you try to upload files > 95mb. For anything larger than this, read the LFS section of the extended tutorial.

<h2> Tutorial </h2>

<h3> Step 1: Install Git </h3>

Go to https://git-scm.com/install/ and install for your operating system. On university machines launch Git from AppsAnywhere.
<br><br> (Note - Git is a free and open source distributed version control system, GitHub is the platform that uses Git.)

Verify your Git installation with:

```
git --version
```

<h3> Step 2: Login to GitHub from your terminal </h3>

When you first install Git, you must run these commands to link your GitHub username and email to your machine.

Run:

```
git config --global user.name "insertyourusername"
```

```
git config --global user.email "your@email.com"
```

<h3> Step 3: Create a GitHub repository</h3>

Go to https://github.com, sign in if prompted. Then navigate to the repositories tab and click create a new repository.

You should be on a page that looks like this: <br>

Create a repository: <br>

<img src="https://res.cloudinary.com/din8rv70n/image/upload/v1770404113/Screenshot_2026-02-06_at_18.55.07_rajgzy.png" alt="drawing" width="650"/>

Once you have named your repo hit create repository at the bottom of the page. You should then be taken to a page that looks like this: <br>

![Link a repository](https://res.cloudinary.com/din8rv70n/image/upload/v1770395943/Link-Repo_mlzfaa.png)

<br> You can stop on this page for now and move on to step 4.

<h3> Step 4: Link your local folder to GitHub </h3>

The whole point of GitHub is to link a local folder to a remote location and track it's changes. Your local folder will act as the main workspace where you write and change your code. You can push your local code to GitHub to save "snapshots" and specific versons onto a remote location.

Open a new terminal at your folder location. If you don't have one, make one.

Initialise your folder with this command:

```
git init
```

You can now run this command to link your local folder to your GitHub repository. Replace username with your GitHub username and reponame with the name of your repository. You can confirm this URL on the page in step 2.

```
git remote add origin https://github.com/username/reponame.git
```

Run this command to create a branch (a branch is like a workspace that does not affect the main project).

```
git branch -M main
```

After running this, you should be prompted to sign in with your GitHub credentials if you haven't already.

Great, now your local folder is now linked to your remote GitHub repository!

<h3> Step 5: Pushing your code to GitHub </h3>

Now that you have your folder and repo linked, you can now "push" your code. This essentialy sends your code from your local folder to your remote repo.

To do this we need to quickly understand the "staging area".

The staging area is the place your code lives when you add files with Git. Think of it like a limbo between your local and remote locations.

So when you run:

```
git add .
```

This adds <ins>every</ins> changed file in your local folder to the staging area.

To add every file, not just the changed ones, run:

```
git add <path>
```

For instance if the path to the folder with all my files was:

```
\Users\Name\Documents\Uni
```

I would run:

```
git add \Users\Name\Documents\Uni
```

You don't always want to add everything, so to add a specific folder or file simply run:

```
git add folderorfilename
```

Now your files are in the staging area we have to commit them with a message.
This should only be done when you have double checked nothing in the staging area will break your repo. <br>

You can check this by running:

```
git status
```

Now you can run:

```
git commit -m "blah blah blah"
```

The commit messages acts as a way to decribe the changes you are making, or what you are adding.

You can check the commit you just made by running:

```
git log
```

To leave the log, press q.

Now we are ready to push.

Run:

```
git push -u origin main
```

Which pushes your local code upstream (-u) to the origin of the main branch.

You can now refresh your GitHub repo and see your files and their commit messages updated. Pretty cool isn't it...

<h2> Key Takeaways </h3>

You want to get into the habit of having your current work folder open in a terminal with a GitHub repository linked to it. <br>
<br>
You can that get used to writing your code and making changes. Then running the golden trio of Git commands:

```
git add
```

```
git commit -m "blah blah"
```

```
git push -u origin main
```

Your local folder should always be the most up to date version (ahead) of your GitHub repo. If you add files to your GitHub repo that don't exist in your local folder, this will break when you next go to push your local code.

Check your if your GitHub repo is ahead by using:

```
git status -uno
```

If it is ahead, run:

```
git pull
```

This syncs your local and remote locations by "pulling" any new files from the GitHub repo to your local folder.

<h2> FAQ and Extended Tutorial</h2>

<h3> How do I go back to a previous version of my code? </h3>

First we need to understand how commits work:

When you commit something a unique identifier called a Git hash is assigned to the commit. <br>

You can view all your commits and their identifiers in the commit tab, seen in the video below:

![](https://res.cloudinary.com/din8rv70n/image/upload/v1770413284/commit_cm0ezs.gif)
<br>

Or you can view this in the terminal by running:

```
git log --oneline
```

Let's say you want to revert or "time travel" back to an old commit. There are a few different ways to do this.

You could temporarily look at or "checkout" the commit by running:

```
git checkout commithashnumber (e.g. 330cdb9)
```

This is fine if you just wanted to look at an old version of your code. But if you wanted to edit it and perhaps commit a change, you would be left in a "detached head state".

This video explains this concept well: https://www.youtube.com/watch?v=Ow3uc-oyhIo

If you did not make any edits when you checked out an old commit, simply switch back to your main branch (or whatever your up to date branch is named) by running:

```
git checkout main
```

Another way to revert back to the previous commit is to use:

```
git revert HEAD
```

Which reverts the code back to the previous commit.

This is good for collaborative repositories, as you are not actually deleting the old commit, so if people need to view/edit it, they can.

For private repositories where no one else is relying on your code you may want to use:

```
git reset HEAD~1
```

This resets your version back to the previous commit with the unstaged code intact.

If you wanted to delete the previous commits unstaged code entirely, use:

```
git reset --hard HEAD~1
```

Okay so now we know how to revert or reset back to the last commit,
but how do we revert or reset back to a specific commit in your repos history.

You can use:

```
git revert 330cdb9
```

Or:

```
git reset Githashnumber^ (make sure to put this ^ at the end of your Git hash number)
```

So an example would look like this:

```
git reset 330cdb9^
```

<h3> How do I make it so certain files are ignored and never pushed to GitHub </h3>

Simply create a .gitingore file, which acts as a set of "rules" that the repository will follow. You can either create it manually, or run:

```
touch .gitignore
```

You can edit your .gitingore file to ignore certain file extensions by adding:

```
*.png
*.jpeg
*.zip
```

If you want to ignore files or folders use:

```
.filename
folder_to_ignore/

```

Then before adding any more files you must

```
git add .gitignore
```

```
git commit -m "Ignoring xyz"
```

```
git push -u origin main
```

The rules you just created have to be pushed otherwise they won't actually be activated.

<h3> I really want to add files bigger than 95mb, how do I do that? </h3>

Git LFS (Large File Storage) is a system that stores a reference of your file instead of the actual file itself—which is stored externally. This allows you to push larger files than the usual limit, but it is still <ins>not</ins> a replacement for cloud storage.

To install Git LFS go to https://git-lfs.com/

To initialise LFS in your folder, run:

```
git lfs install
```

Now you can start tracking folders or files to store with LFS.

```
git lfs track "yourlargefileorfolder"
```

To check which files/folders are tracked by LFS, run:

```
git lfs ls-files --all
```

Like with a .gitignore file, make sure to commit these changes <ins>before</ins> you add the large files to the staging area, otherwise they won't be stored with LFS.

If you have already added large files to the staging area, see the below section on how to fix that.

<h3> I have accidentally added files to the staging area and now I can't undo it? </h3>

To unstage a specfic file, you can run:

```
 git reset filename.xyz
```

To unstage all files ending in that extension, run:

```
git reset *.extensionname
```

Or simply:

```
git reset
```

To unstage all files in the staging area.

<h3> Why can't I just drag and drop my files into GitHub instead of this command line stuff? </h3>

1. It's illegal. <br>
2. It's incredibly inefficient, instead of writing a few commands (that do become muscle memory) you have to waste time in a GUI.

So yeah call me a nerd all you like but if this was helpfull you owe me a drink :+1:.
