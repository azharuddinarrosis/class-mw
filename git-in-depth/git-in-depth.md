#Git in depth

Source: https://frontendmasters.com/courses/git-in-depth/
Learning objectives: understand the concept of using git properly and correctly

➤ What is Git? `Distributed Version Control System`

Git (/ɡɪt/) is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development. (source) , git stores the compressed data in blobs with metadata in the headers and generates this data using SHA1.


➤ Working Area, Staging Area, Repository
	

1.	Working area 

    This file in local area or only in your device (untracked file), in there u can modify your content

2.	Staging area

    This area used for thats file are going to be part of the next commit. this area know change between current commit and next commit

3.	Repository

    This area contains all commits and contains all files you have committed in git

➤ Staging Area Deep Dive

Three areas where code lives : working area (or sometimes called as working tree), staging area (or cache or index) and repository. The working area are the files in your working area that are not in staging area and not handled by git, basically the files in your local directory in your computer. The staging area is how git knows what will change between the current commit and the next commit. The repository contains all your commits. Git stash is used to save un-committed work and safe from git destructive operation like changing branches while in the middle of work or overwriting file. And you can apply it back to your branch anytime when needed.
	
➤ References, Commits, Branches
    
1. References

	References are pointers to commits. We already learned that there are three types of Git references. Tags, annotated tags, branches, and HEAD. So now let's talk about, let's get a little bit philosophical. What is a branch? So a branch, it's just a pointer to a particular commit. The pointer to the current branch is going to change.

	- Reference have 3 type 

	 -  HEAD    

		What is HEAD? HEAD is how Git knows what branch you're currently on. But most importantly, HEAD is how Git knows what the parent of the next commit will be. It's kind of effectively a sim link to the branch that you're currently working on.

			How to check reference 

				You can check in this file `.git/HEAD `

	 -  Tag   

			One of the other types of refs that we can have is a lightweight tag. Those are just a simple pointer to a commit

			Create new tag `git tag -a`
			Show all tag ` git show-ref –tags`
	 -  Remotes    

		The third type of reference that you’ll see is a remote reference. If you add a remote and push to it, Git stores the value you last pushed to that remote for each branch in the refs/remotes directory. For instance, you can add a remote called origin and push your master branch to it

		` git remote add origin git@github.com:{username}/{repository} git`

2. Commit

	Git commit is used to save every code change, before we commit we are required to do git add which will be used to provide tags or details of changes that have been made,

	There are some things that can't be done after we commit

	-  Can't change this commit 
	-  Can't edit
	-  Can't go back
	-  Can't change the author
	-  Can't change the date

	Because we make new changes to the code, we will get a different sha1 with the previous commit

3. Branches

	Using a Git branch is a great way to work on your app while keeping track of each version. In general, a development branch is a bifurcation of code states that create new paths for its evolution. This branch can be paralleled to any other Git branch you create. As is well known, you can incorporate new functions into your code regularly and appropriately.

	Using Git Branches has many advantages. However, we would like to emphasize the following 2 advantages:

	1.	Allows development of new features for applications without interrupting development on the main branch.
	1.	Allows the creation of different development branches that can be centralized in one repository. For example stable branch, test branch and unstable branch.

➤ Stashing

The git stash is a way to save uncommitted work. The stash is pretty safe from most disruptive git operations, and it's handy for so many things. For example, switching between branches while you're in the middle of work.
        
Git stash, stash and git stash list, show what's in your stash. Now, when you git stash list, you will see a bunch of references that kind of look like this, stash . You can actually refer to that as a reference.	

When you can use git stash, If you're using operations that can delete or overwrite your changes like git reset or git checkout, that might also be a good time to stage your changes

Commands in git stash:

1. Command for stashing your code

        `git stash`

2. Command for how to show your list stash

        `git stash list`

3. Command for how to show your list stash

        `git stash list`

4. Command for show your content in your list stash

        `git stash show stash@{n}`

5. Command for apply ur last stash
    
        `git stash apply`

6. Command for apply ur specific stash

        `git stash apply stash@{n}`
    
7. Command for stashing untracked files

        `git stash --include-untracked`

8. Command for stashing all files
        
        `git stash --all`

9. Command for delete last stashing and applying change
        
        `git stash pop`

10. Command for delete last stash
    
        `git stash drop`
    
11. Command for delete specific stash
        
        `git stash drop stash@{n}`

12. Command for delete all stash
        
        `git stash clear`


➤ Merging 

The git merge tool is used to merge one or more branches into the branch you have checked out. It will then advance the current branch to the result of the merge.



➤ Rebase

If <branch> is specified, git rebase will perform an automatic git switch <branch> before doing anything else. Otherwise it remains on the current branch.

If <upstream> is not specified, the upstream configured in branch.<name>.remote and branch.<name>.merge options will be used (see git-config[1] for details) and the --fork-point option is assumed. If you are currently not on any branch or if the current branch does not have a configured upstream, the rebase will abort.

 - Imagine our tech_posts and master branch have diverged.
- We don’t want a messy merge commit in our history.
- We can pull in all the latest changes from master, and apply our commits on top of them by changing the parent commit of our commits.

			Rebase = give a commit a new parent

➤ Forks & Remote Repositories

Fork 

- 	The concept of forking a project has existed for decades in the world of free and open source software. To "fork" means to copy a project, change its name, and create a project and community with the copy. People who fork rarely contribute back to the main project.

Remote Repositories
-		 When we have a project, of course we want to keep all the files in it. Also, you can still edit or add new files in your project without worry, by tracking the changes you make.

-		 Using git is very helpful, but the repository is stored on our own local computer. Then what if there is an unexpected incident with our computer, I hope it never happens. But it will be very safe if we use hosting for our project, besides being safe we can also access it anywhere.



➤ The Danger Zone

-				danger zone where you can tell all the code if you use git wrong, therefore you have to make a config that will keep the code stable,

➤ Advanced Tools

➤ Customization - Config, Ignore, Hooks, Templates
1. Config 

	-			 You typically configure your global username and email address after installing Git. However, you can do so now if you missed that step or want to make changes. After you set your global configuration, repository-specific configuration is optional.
	
			Git configuration works the same across Windows, macOS, and Linux.

		-				**To set your global username/email configuration**

						1.	Open the command line.
						
						2.	Set your username:
						`git config --global user.name "FIRST_NAME LAST_NAME"`
						
						2.	Set your email address:
						`git config --global user.email "MY_NAME@example.com"`
						
		-				**To set repository-specific username/email configuration:**
						1.	From the command line, change into the repository directory.

						2.	Set your username:
						`git config user.name "FIRST_NAME LAST_NAME"`

						3.	Set your email address:
						`git config user.email "MY_NAME@example.com"`

						3.	Verify your configuration by displaying your configuration file: cat `.git/config`
	
2. Ignore

	-			 Git sees every file in your working copy as one of three things:
			1.		tracked - a file which has been previously staged or committed;
			2.		untracked - a file which has not been staged or committed; or
			3.		ignored - a file which Git has been explicitly told to ignore.

		Ignored files are tracked in a special file named .gitignore that is checked in at the root of your repository. There is no explicit git ignore command: instead the .gitignore file must be edited and committed by hand when you have new files that you wish to ignore. .gitignore files contain patterns that are matched against file names in your repository to determine whether or not they should be ignored.
		
3. Hooks

	-			 Git hooks are scripts that run automatically every time a particular event occurs in a Git repository. They let you customize Git's internal behavior and trigger customizable actions at key points in the development life cycle.

4. Templates  

	-			 Templates in Git are the starting files and settings for all new Git repositories. Any files not starting with a dot (hidden files) will be copied to the new Git repository upon initialization. 


➤  Integrating Git 
-					 there are several tools that can be integrated with git, for example
github action, circleCI and others

➤  Git Rerere
-					 Git Rerere, which stands for Reuse Recorded Resolution is a really, really helpful tool.What it does is when it's turned on, git's gonna save how you resolved a conflict. And next conflict, it's just gonna reuse that same resolution. It's really useful for things like a long lived feature branch, like a refactor, or when you're rebasing. Has anyone tried a rebase, and then every time you rebase,




