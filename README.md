# Git Introduction
This project will help you dip your toes into using Git in a collaborative setting. We will focus on using remote repositories, pushing/pulling, branches, and resolving conflicts!

NOTE: You will be working in pairs to simulate the code collaboration experience. Assign someone to be Person A and the other to be Person B. MAKE SURE that you work side-by-side to see all parts of the Git process.

## Part 0 - Person A only

1. Visit https://github.com/joonyoo181/plextech-git-intro
2. On the main page, click the fork button on the upper right hand corner that should take you to the "Create a new fork" page
3. Make sure the Owner is your Github account and then click the green "Create fork" icon
4. Navigate back to the main page of YOUR NEW FORKED REPOSITORY and click the green "<> Code" icon
5. Click the copy link icon for under the HTTPS tab to copy the link for your forked repo
6. Type the following commands in a new folder on your local machine. This will be the folder where you store your projects:
    1. `git clone <link-copied-in-step-5> plextech-git-intro`
      ^ This clones Jeremy's remote repository into a local folder called "plextech-git-intro"

Open this folder in VS Code! You should now be able to see the starter code.

### PART 1 - Person B only

Clone down Person A's repository (MAKE SURE PERSON B HAS INVITED YOU TO THE GIT REPO FIRST!) by visiting their forked Github link for their intro projects and following the same instructions for cloning:

1. Navigate back to Person A's forked main page and click the green "<> Code" icon
2. Click the copy link icon for under the HTTPS tab to copy the link for your forked repo
3. On your terminal/bash, create a new folder anywhere outside of your forked repo.
4. Type the following commands in a new folder on your local machine.
    1. `git clone <link-copied-in-step-2> plextech-git-intro`
      ^ This clones Person A's remote repository into a local folder called "plextech-git-intro"

Open this folder in VS Code! Open a terminal in VS Code and type `git log` and save a screenshot in this folder.

When working on projects, you are going to be constantly pushing and pulling code to update/get updates from your repos. Let's push the screenshot that we just created to our repository.
A "commit" is a list of changes that is stored by git. Committing only affects your local Git record.

1. Type `git status` to see the new change created by your added image. It should be called `<SCREENSHOT-NAME-1>.png/jpy/slay`
2. Type `git add <SCREENSHOT-NAME-1>.png/jpy/slay` to stage the file.
3. Type `git commit -m "image added by <your-name>"` to commit your change.
4. Type `git push origin main` to push your changes to the main branch.
  ^ This pushes your changes to a remote repository called "origin" and its branch "main". The name "origin" is an alias for this project's repository and it got set when you did `git clone`. Talk to a CI if you have more questions.

Now when you navigate to the repository on your Github, you should see all the starter code along with your screenshot in the project folder. Now if Person A wanted to keep working with you on this project, they would need to `git pull` the changes whenever you update the repository on your end to avoid any major merge conflicts.

### PART 2 - Person A ONLY

Lets try doing the same workflow that Person B did:

Type `git log` and save a screenshot in this folder.

When working on projects, you are going to be constantly pushing and pulling code to update/get updates from your repos. Let's push the screenshot that we just created to our repository.
A "commit" is a list of changes that is stored by git. Committing only affects your local Git record.

1. Type `git fetch --all` to make sure your local version of the remote main branch is updated
2. Type `git status` to see the new change created by your added image. It should be called `<SCREENSHOT-NAME-2>.png/jpy/slay`
3. Type `git add <SCREENSHOT-NAME-2>.png/jpy/slay` to stage the file.
4. Type `git commit -m "image added by <your-name>"` to commit your change.
5. Type `git push origin main` to push your changes to the main branch.
  ^ This pushes your changes to a remote repository called "origin" and its branch "main". The name "origin" is an alias for this project's repository and it got set when you did `git clone`. Talk to a CI if you have more questions.

Whoops! You hopefully got some error message along the lines of "Updates were rejected because the remote contains work that you do not have locally." This means that your local version of the LOCAL main branch does not have the changes that Person B pushed up earlier, so we can't push our changes until we take Person B's changes in first. All we have to do is:

1. Type `git pull origin main` to pull changes from the remote main branch from Person B into the local main branch.
2. Type `git push origin main` to push your changes to the main branch. There should be no errors this time! If you still face error, get help from a CI!

## Branching
Typically when you are working on a larger project with multiple developers, you will be working on a separate branch specific to the feature that you are responsible for. This allows for independent lines of development, as new additions can be made to the main repository without pushing unfinished code from another feature. Let's use this feature for the last part of this project.

### Part 3 - Person B ONLY

Suppose one of your project partners created `foo.py` with a function that prints "Foo" if the input is a multiple of 3 and "Bar" otherwise. However, you found that the function only works with positive numbers up to 30. Your job is to fix this bug while your partner is working on another feature.

1. First type `git pull origin main` to get Person A's latest change in (Their latest change should be adding their screenshot to the project directory).
  a. Ensure that you have Person A's changes by doing `git log` and seeing their commit message "image added by <person-b-name>"
2. Create and checkout a new branch with `git checkout -b bug-fix`. If you type `git branch` you should see your new branch with a * next to it to indicate that is your current working branch.
3. Fix the function in `foo.py` so that it works as intended.
4. Add and commit your changes.
5. Type `git push origin bug-fix` to push your changes to the new branch that you created.

### Part 4 - Person A ONLY

Person B has fixed the bug in the code, but now what? These changes are still in your bug-fix branch, while the issue is still not resolved on main. What we want to do is merge the fixes in our current branch into the main branch of our repository. We can do so through a ***pull request***.

1. On your Github repository, click on "pull requests" and then "new pull request." Select your bug-fix branch as the compare branch and click "create pull request" (make sure main is the base branch). Here, reviewers can comment on the changes that you've made and approve the pull request before it gets merged into the main codebase.
  a. In most companies, PRs (short for pull requests) often have to be approved by multiple people at different levels (Senior Engineers, Managers, etc) before getting merged. This is where other people can comment on your code/suggest things to change/have discussions on your code.
  b. Additionally at some companies, there are things called CI (continuous integration) / CD (continuous development) checks that automatically run unit test cases/integration test cases on every PRs. At Roblox, they had ~50 checks that took 1+ hours to finish and all checks had to pass (on top of being reviewed by others) before you could merge.
2. Add a comment onto the pull request (like a "LGTM" or something quirkier!??!)
3. Click "merge pull request" and confirm the merge.

Now you should be able to see your changes on main.

## Conclusion

YAYYY CONGRATS! You just finished PlexTech's first project! How do you feel? Hopefully, you got to learn a little more about how Git is used in a team setting. Throughout this semester, we will be incorporating a lot of these concepts into our own workflow. Get excited :))
