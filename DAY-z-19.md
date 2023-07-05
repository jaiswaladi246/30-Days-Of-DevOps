# DAY-19 | GIT 

Git is a distributed version control system that allows multiple developers to collaborate on a project, tracking changes to files and managing different versions of the codebase. Here's a brief explanation of how Git works:

### Repositories
A Git repository is a directory or folder that contains your project's files, as well as the entire history of changes made to those files. It acts as a central hub for collaboration.

### Commits
In Git, a commit represents a snapshot of your project at a specific point in time. Each commit is associated with a unique identifier (a hash) and contains information such as the author, timestamp, and a message describing the changes made in that commit.

### Branches
Git allows you to create branches, which are independent lines of development. Each branch can have its own commits, allowing multiple developers to work on different features or bug fixes simultaneously. Branches make it easy to experiment, collaborate, and merge changes back into the main codebase.

### Working Directory, Staging Area, and Repository
Git has three main areas:

1. Working Directory: This is the directory on your local machine where you modify and create files.

2. Staging Area (Index): The staging area is an intermediate area where you select and stage the changes you want to include in the next commit. You can think of it as a holding area for changes you want to commit.

3. Repository: The repository is where Git stores the complete history of your project, including all the committed changes. It is usually located in the hidden `.git` folder within your project directory.

### Basic Workflow
The typical Git workflow involves the following steps:

1. Initialize a repository: Use `git init` to create a new Git repository in your project directory, or `git clone` to clone an existing repository.

2. Add and commit changes: Use `git add` to stage changes from your working directory to the staging area. Then use `git commit` to create a new commit with the staged changes, along with a descriptive commit message.

3. Create and switch branches: Use `git branch` to create a new branch, and `git checkout` to switch to a different branch.

4. Merge branches: Use `git merge` to merge changes from one branch into another. This combines the commits from both branches into a single branch.

5. Push and pull changes: Use `git push` to upload your local commits to a remote repository, and `git pull` to fetch and integrate remote changes into your local repository.

## Here are some commonly used Git commands with examples
### Initialize a Git repository

Command:
```
git init
```

Example:
```
$ git init
Initialized empty Git repository in /path/to/repository/.git/
```

### Clone a repository

Command:
```
git clone <repository_url>
```

Example:
```
$ git clone https://github.com/username/repository.git
Cloning into 'repository'...
remote: Enumerating objects: 25, done.
remote: Counting objects: 100% (25/25), done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 25 (delta 6), reused 22 (delta 5), pack-reused 0
Unpacking objects: 100% (25/25), done.
```

### Stage changes

Command:
```
git add <file_name>
```

Example:
```
$ git add index.html
```

### Commit changes

Command:
```
git commit -m "Commit message"
```

Example:
```
$ git commit -m "Add initial version of index.html"
```

### Create a new branch

Command:
```
git branch <branch_name>
```

Example:
```
$ git branch feature/add-new-feature
```

### Switch to a branch

Command:
```
git checkout <branch_name>
```

Example:
```
$ git checkout feature/add-new-feature
```

### Push changes to a remote repository

Command:
```
git push <remote_name> <branch_name>
```

Example:
```
$ git push origin main
```

### Pull changes from a remote repository

Command:
```
git pull <remote_name> <branch_name>
```

Example:
```
$ git pull origin main
```

### Merge a branch into the current branch

Command:
```
git merge <branch_name>
```

Example:
```
$ git merge feature/add-new-feature
```

### View commit history

Command:
```
git log
```

Example:
```
$ git log
commit a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
Author: John Doe <john.doe@example.com>
Date:   Mon Jul 05 12:34:56 2023 +0300

    Add initial version of index.html

commit b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q
Author: Jane Smith <jane.smith@example.com>
Date:   Sun Jul 04 09:12:34 2023 +0300

    Update README.md
```

These are just a few examples of commonly used Git commands. There are many more commands and options available for different use cases. You can refer to the official Git documentation for more information: [Git Documentation](https://git-scm.com/doc)
