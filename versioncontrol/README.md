# Git Pre-Workshop Assignment

### Instructions
- Read step 1 to get a high-level intro to version control. Don't overthink it.
- OPTIONAL (but super useful) configure your terminal or IDE to show the git status - [instructions here](GITTERMINAL.md).
- Follow the instructions in steps 2-6. 
    - They are meant to make you look up some new commands - when you see the emoji 🔍, it will be a hyperlink to helpful resources on commands - click it!
    - In general, *your computer already has all the answers you need* - read the outputs of all commands carefully.
- Check the following resources after you are done for additional reading and prep if you'd like:
    - https://www.atlassian.com/git/tutorials/what-is-version-control

1. **Introduction to Version Control**:

   - **What is Version Control?** Version control is a system that records changes to files over time so that you can recall specific versions later. It helps in tracking modifications, collaborating with others, and managing different versions of your work.
   - **Why Use Version Control?** Imagine working on a project where multiple people are editing files simultaneously. Version control prevents chaos by allowing everyone to make changes without overwriting each other’s work. It also helps track who made what change and provides a way to revert to earlier versions if needed.
   - **Collaboration Made Easy**: With version control, team members can work independently on different features or sections, and later combine (or merge) their changes seamlessly. This is crucial when multiple people contribute to a project.
   - **Avoiding Loss of Work**: Mistakes happen, and version control systems like Git allow you to revert to a previous version if something goes wrong. This safety net ensures that your work is always recoverable.
   - **Accountability and Tracking**: Version control allows you to track changes, see who made them, and understand why they were made through commit messages. This creates transparency and accountability in team projects.

2. **Setup and Configuration**:

   - **Step 1: Open Your Terminal**

   - **Step 2: Install Git** (check installation status first [🔍](https://www.google.com/search?q=what+is+the+--version+option))

     ```sh
     git --version
     brew install git
     ```

   - **Step 3: Configure Your User Information**

     This tells Git who you are, which helps keep track of who makes changes.

     ```sh
     git config --global user.name "Your Name"
     git config --global user.email "yourname@example.com"
     ```

   - **Step 4: Check Your Configuration**

     ```sh
     git config --list
     ```

3. **Making Your First Commits**:

   - **CRUCIAL: Your new best friend: `git status`** [🔍](https://github.com/git-guides/git-status)
       - Try running it *before* step 1 - you will get an error [🔍](https://www.gitkraken.com/learn/git/tutorials/what-is-a-git-repository)
       - After **Step 1**, you should get in the habit of running it all the time to see whats going on
       - Shows the current status:
            - What is in the staging area
            - What is tracked or untracked

   - **Step 1: Initialize a Repository** [🔍](https://www.google.com/search?q=basic+file+navigation+in+terminal)

     ```sh
     mkdir my_first_project
     cd my_first_project
     git init
     ```

   - **Step 2: Add Files and Make Your First Commit** [🔍](https://www.google.com/search?q=what+is+the+echo+command+terminal)

     ```sh
     echo "Hello, Git!" > README.txt
     git add README.txt
     git commit -m "Initial commit: added README"
     ```

   - **Step 3: Explore and Mess Around** [🔍](https://www.google.com/search?q=how+to+use+git+log)

     ```sh
     echo "Updated content." >> README.txt
     git add README.txt
     git commit --amend -m "Updated README"

     git log --oneline

     echo "Another update." >> README.txt
     git add README.txt
     git commit -m "Added more content to README"

     git log --graph --decorate --oneline

     echo "Final update." >> README.txt
     git add README.txt
     git commit -m "Final update to README"

     git log --all --graph --decorate --oneline
     ```

4. **Working with Remotes**:

   - **What is a Remote?** A remote is a version of your project that is hosted on another server, such as GitHub, which allows you to collaborate with others. Git is a distributed version control system (VCS), meaning every developer has a full copy of the repository on their machine. By default, your local Git repository doesn't know about any remotes until you explicitly add them.

   - **Step 1: Create a Remote Repository**: Go to GitHub and create a new repository [🔍](https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories). This will be your first example of a remote repository.

   ```sh
   git remote add origin https://github.com/yourusername/my_first_project.git
   ```

   - **Step 2: Push Your Commits**

   ```sh
   git push -u origin main
   ```

5. **Branching and Merging:**

    - **Step 1: Create a New Branch**

    ```sh
    git branch new-feature
    git switch new-feature
    ```

    - **Step 2: Make Changes and Merge Back**

    ```sh
    echo "Branch feature content" >> feature.txt
    git add feature.txt
    git commit -m "Add feature file"
    git switch main
    git merge new-feature
    ```

6. **Conflict Resolution**:

    - **Step 1: Simulate a Merge Conflict**

      Create a scenario where both `main` and `new-feature` branches modify the same line of `README.txt`.
      ```sh
      git switch main
      echo "Change on main branch" >> README.txt
      git add README.txt
      git commit -m "Main branch update"

      git switch new-feature
      echo "Change on new-feature branch" >> README.txt
      git add README.txt
      git commit -m "New feature branch update"
      ```

    - **Step 2: Attempt to Merge and Resolve Conflict**

      Attempt to merge the `new-feature` branch back into `main` and resolve the conflict that arises.
      ```sh
      git switch main
      git merge new-feature
      ```

    - **Step 3: Push the Resolved Changes to Remote**

      After resolving the merge conflict, commit and push the changes to the remote repository.
      ```sh
      git add README.txt
      git commit -m "Resolved merge conflict"
      git push origin main
      ```
