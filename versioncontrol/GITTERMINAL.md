#OPTIONAL: Set Up Your Terminal to Reflect Git Status**

To make your terminal reflect the current Git status (branch, etc.), follow these steps based on your operating system or editor. Note that there are many different ways to do this, and different shells to configure your terminal with more similar features outside of git, and make it look very pretty. I chose the simplest route here for each OS - just follow the instructions so you have the visual terminal working for git for the workshops, you can completely change all of this later and personalize it more if you are interested.

- **Linux/macOS**:
  - Use
  ```sh
  curl -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
  source ~/.git-prompt.sh
  export PS1='\\u@\\h \\W$(__git_ps1 " (%s)")\\$ '
  ```

- **Windows**:
  - Use **Git Bash**, which comes with Git for Windows.
  - Alternatively, use **Windows Terminal** and configure it with **oh-my-posh** to display Git information.
  ```sh
  Install-Module posh-git -Scope CurrentUser
  Install-Module oh-my-posh -Scope CurrentUser
  ```

- **VS Code**:
  - Install the **GitLens** extension from the Extensions Marketplace.

