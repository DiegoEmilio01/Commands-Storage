# [Git](https://git-scm.com/)

## Upload local changes

| Command                   | Description                                           |
| -------------             | :-------------                                        |
| `git status`              | Compare local repository with its online counterpart. |
| `git add --all`           | State which changes are ready to upload.              |
| `git commit -m "message"` | Generate a commit with its message.                   |
| `git push`                | Send the commit to the repository on [GitHub](https://github.com/). |
| `git revert hash_commit`  | Revert the repository to a previous commit. |

## Branches and workflow

| Command                       | Description                     |
| -------------                 | :-------------                  |
| `git checkout -b new_branch`  | Create the branch `new_branch`. |
| `git checkout name`           | Change to branch `name`.        |
| `git branch`                  | Print a list of all branches.   |
| `git branch -d name`          | Delete branch `name`.           |
| `git push origin name`        | Analogous to `git push`. Then a pull request has to be created and a merge executed. |

## Delete sensitive information from all version

[Github oficial documentation](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/removing-sensitive-data-from-a-repository)