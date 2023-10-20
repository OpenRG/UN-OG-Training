(Chap_GitIntro)=
# Git and GitHub

Two warnings that a seasoned Git and GitHub user should always give a new entrant to this type of version control and code collaboration are the following.
* The learning curve is steep.
* The workflow initially is not intuitive.

These two obstacles seem to work together to make this form of collaboration harder than the sum of their parts initially. However, once you begin collaborating on open source projects or on large-group academic or research projects, you start to see the value of all the different steps, methods, and safeguards invoved with using Git and GitHub. {numref}`Figure %s <GitFlowDiag>` below is a diagram of the main pieces and actions in the primary workflow that we advocate in this book. You will notice that a version of this figure is the main image for the book and is also the `favicon` for the tabs of the web pages of the online book. This figure of a Git and GitHub workflow diagram looks complicated, but these actions will become second nature. And following this workflow will save the collaborators time in the long-run.

```{figure} ./images/GitFlowDiag.png
---
scale: 50%
align: center
name: GitFlowDiag
---
Flow diagram of Git and GitHub workflow
```


## Brief definitions

```{admonition} Definition: Repository
:class: note
A {term}`repository` or "repo" is a directory containing files that are tracked by a version control system. A local repository resides on a local machine. A {term}`remote` repository resides in the cloud.
```

```{admonition} Definition: Git
:class: note
{term}`Git` is an {term}`open source` {term}`distributed version control system` (DVCS) software that resides on your local computer and tracks changes and the history of changes to all the files in a directory or {term}`repository`. See the Git website [https://git-scm.com/](https://git-scm.com/) and the [Git Wikipedia entry](https://en.wikipedia.org/wiki/Git) {cite}`GitWiki2020` for more information.
```

```{admonition} Definition: GitHub
:class: note
{term}`GitHub` or [*GitHub.com*](https://github.com/) is a {term}`cloud` {term}`source code management service` platform designed to enable scalable, efficient, and secure version controlled collaboration by linking {term}`local` {term}`Git` version controlled software development by users. *GitHub*'s main business footprint is hosting a collection of millions of version controlled code repositories. In addition to being a platform for {term}`distributed version control system` (DVCS), *GitHub*'s primary features include code review, project management, {term}`continuous integration` {term}`unit testing`, {term}`GitHub actions`, and associated web page (GitHub pages) and documentation hosting and deployment.
```

To be clear at the outset, Git is the version control software that resides on your local computer. It's main functionalities are to track changes in the files in specified directories. But Git also has some functionality to interact with remote repositories. The ineraction between Git and GitHub creates an ideal environment and platform for scaleable collaboration on code among large teams.

## Wide usage
Every year in November, GitHub publishes are report entitled, "The State of the Octoverse", in which they detail the growth and developments in the GitHub community in the most recent year. The most recent [State of the Octoverse](https://github.blog/2019-11-06-the-state-of-the-octoverse-2019/) was published on November 6, 2019 and covered developments from October 1, 2018 to September 30, 2019. Some interesting statistics from that report are the following.

* more than 40 million GitHub user accounts
* more than 100 million code repositories

Alternatives to GitHub include [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/). Other alternatives are documented in [this June 2020 post](https://www.softwaretestinghelp.com/github-alternatives/) by Software Testing Help. But GitHub has the largest user base and largest number of repositories.


(chap_basics)=
# Git and GitHub basics

Create, clone, fork, remote, branch, push, pull, pull request.

Include a discussion of `git pull` vs. `git pull --ff-only` vs. `git pull --rebase`. A good blog post is "[Why You Should Use git pull –ff-only](https://blog.sffc.xyz/post/185195398930/why-you-should-use-git-pull-ff-only)" by Shane at ssfc's Tech Blog.


(chap_cheatsheet)=
# Git and GitHub Cheat Sheet

About 99% of the commands you'll type in `git` are summarized in the table below:


| Functionality                                               | Git Command                                                      |
|-------------------------------------------------------------|------------------------------------------------------------------|
| See active branch and uncommitted changes for tracked files | `git status -uno`                                                  |
| Change branch                                               | `git checkout <branch name>`                                       |
| Create new branch and change to it                          | `git checkout -b <new branch name>`                                |
| Track file or latest changes to file                        | `git add <filename>`                                               |
| Commit changes to branch                                    | `git commit -m "message describing changes" `                      |
| Push committed changes to remote branch                     | `git push origin <branch name>`                                |
| Merge changes from master into development branch           | `(change working branch to master, then…) git merge <branch name>` |
| Merge changes from development branch into master           | (change to development branch, then…) `git merge master`           |
| List current tags                                           | `git tag`                                                          |
| Create a new tag                                            | `git tag -a v<version number> -m "message with new tag"`           |
| Pull changes from remote repo onto local machine            | `git fetch upstream`                                               |
| Merge changes from remote into active local branch          | `git merge upstream/<branch name>`                                 |
| Clone a remote repository                                   | `git clone <url to remote repo>`                                  |



(SecGitIntroFootnotes)=
## Footnotes

<!-- [^citation_note]: See {cite}`AuerbachEtAl:1981,AuerbachEtAl:1983`, {cite}`AuerbachKotlikoff:1983a,AuerbachKotlikoff:1983b,AuerbachKotlikoff:1983c`, and {cite}`AuerbachKotlikoff:1985`. -->
