# schotter

You need the following tools:

- [Git](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Python](https://www.python.org/downloads/)

They may already be installed on the computers in the V915 lab. You will probably need to install them on your own computer.

### macOS

If you do not have Homebrew, install it by following the instructions on the [Homebrew website](https://brew.sh/). Then run:

```bash
brew install git
brew install --cask visual-studio-code
```

macOS may offer to install the Xcode Command Line Tools when you first run `git`. That version also works, although the Homebrew version is usually newer.

### Windows

Download and install the tools from their official websites:

- [Git for Windows](https://git-scm.com/download/win)
- [Visual Studio Code](https://code.visualstudio.com/download)
- [Python for Windows](https://www.python.org/downloads/windows/)

When installing Python, select **Add Python to PATH** if the option is available.

### Check the Installation

Open a new terminal. In VS Code, use ``Ctrl+` `` on Windows or ``Cmd+` `` on macOS. Run:

```bash
git --version
python --version
```

On Windows, you may need to use:

```powershell
py --version
```

If each command prints a version number, the installation worked. If you see `command not found` or a similar error, check the installation and open a new terminal before trying again.

### Tell Git Who You Are

Git records your name and email address in every commit. Configure them once with:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Replace the examples with your real name and the email address connected to your GitHub account. If the email addresses do not match, your commits will still work, but GitHub may not connect them to your profile or contribution graph.

If you do not want your real email address to be public, open **Settings → Emails** on GitHub, enable **Keep my email addresses private**, and use the `noreply` email address provided by GitHub.

Check your configuration with:

```bash
git config --global user.name
git config --global user.email
```

## 4. Clone the Course Repository

Open a terminal and run:

```bash
cd Documents
git clone https://github.com/sd5913/pfad
cd pfad
code .
```

You may use a different directory if you already have a dedicated place for your course projects.

Before class each week, open the course repository and download the latest material:

```bash
git pull
```

### Explore the Branches

The course repository has two branches:

- `2026` contains this year's course material.
- `2025` contains all thirteen weeks of last year's material.

List all available branches:

```bash
git branch -a
```

Switch to last year's material:

```bash
git switch 2025
ls
```

Switch back to this year's branch:

```bash
git switch 2026
```

Notice how the files in your working directory change when you switch branches. You do not need to download them again: `git clone` copied the complete repository, including its branches and history.

If you want to look ahead to Assignment 2, the Week 1 web-scraping example is located at `week01/main.py` on the `2025` branch.

You will use branches more extensively during the group project, when several people need to work on the same code without overwriting one another.

### Understand Read-Only Repositories

You can read the course repository, but you do not have permission to push changes directly to it. A rejected `git push` is therefore expected and is not an error in your setup.

There are two common ways to contribute to a repository you cannot write to:

1. **Open an issue:** If you find an error or something unclear, report it in the [course repository issues](https://github.com/sd5913/pfad/issues). Explain what you did, what you expected, and what happened.
2. **Fork and open a pull request:** If you have fixed the problem, fork the repository to your own account, commit the fix there, and open a pull request to the course repository.

> [!CAUTION]
> `git reset --hard` permanently discards uncommitted local changes. Only run the following command when you are certain that you do not need to keep your experiment.

To restore your current course branch after testing its write permissions:

```bash
git reset --hard origin/$(git branch --show-current)
```

## 5. Create Your First Repository

You will now publish a piece of generative art called *Schotter* and use Git to record how it changes.

### 5.1 Create the Repository on GitHub

Open [GitHub's new repository page](https://github.com/new) and use the following settings:

- **Owner:** Your personal account
- **Repository name:** `schotter`, or another lowercase name using hyphens instead of spaces
- **Visibility:** Public
- Select **Add a README file**

Click **Create repository**.

### 5.2 Clone the Repository and Add the Sketch

Replace `YOUR-USERNAME` with your GitHub username:

```bash
cd ..
git clone https://github.com/YOUR-USERNAME/schotter
cd schotter
```

Copy `week01/first-repo/sketch.py` from the course repository into your new project.

On macOS:

```bash
cp ../pfad/week01/first-repo/sketch.py .
```

In Windows PowerShell:

```powershell
Copy-Item ..\pfad\week01\first-repo\sketch.py .
```

Run the program:

```bash
python sketch.py
```

On Windows, you may need to run:

```powershell
py sketch.py
```

The program creates `sketch.svg`. Double-click the file, or open it in your browser, to view the result.

The piece is a homage to Georg Nees' 1968 work *Schotter*, one of the earliest examples of computer-generated art. Its squares begin in an orderly grid at the top and become increasingly chaotic toward the bottom.

### 5.3 Commit and Push
