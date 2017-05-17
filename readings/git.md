# Intro to Git (and GitHub)

## Exercises

* [Try Git][try-git], interactive 15 minute Git introduction by GitHub and Code School.

## Readings
The best intro to Git is Chacon's [Pro Git][pro-git]. Read the
following sections:

* ch1
  * Don't bother installing git from source
  * You'll want to set your user name and email address
  * Mac users can install through Macports
* ch2 (skip 2.6)
  * Before section 2.5, sign up for a github account set up your ssh
    keys. See more below.

Lastly, also watch this [video demo][vimeo-demo] of git being used for
a project.

[vimeo-demo]: http://vimeo.com/16395537

## Pro Git Reading Guide
### ch1
* What is version control?
* What is a DVCS?
* How does Git think about data? Explain the difference between
  snapshots and differences.
* What are the three main states that your files can reside in? Be
  able to explain each stage in a single sentence.
* What are the three main sections of a Git project? Again, be
  able to explain each section in a single sentence.
* How do you call up a manual page for a command?

### ch2

**Creating repos**:
* How do you initialize a git repository in an existing project?
* How do you use `git clone` to clone an existing repository?
  * For practice, clone the Rails repository on github

**Comparing, adding, and committing files**:
* How do you use `git status` to check the status of the files in your
  git repo?
* How do you check what staged and unstaged changes there are to files?
  * What is the difference between `git diff` and `git diff --cached`?
* How do you stage files for tracking by git?
  * How do you stage a single file?
  * How do you stage all the files with outstanding changes in the
    repo? (`git add -A`)
  * How do you stage all the files with outstanding changes in the current directory? (`git add .`)
  * How do you stage files or chunks of files in patch mode? (`git add
    -p`)
* How do you make a commit once you have staged files?
* How do you tell git to ignore certain files or directories?
* How do you remove a file from your git repo?
* Know how to use `git mv` instead of `mv` followed by `git rm` and
  `git add`.
* How do you amend your previous commit?
* How do you unstage a staged file?
  * How do you unstage all the staged files?
* How do you "unmodify" a modified file using `git checkout`? (`git checkout filename.rb`)

**Viewing previous commits**:
* How do you list the previous commits (`git log`)? To view 'all' logs, e.g. view branches on remote repos (`git log --all`)
* Your readings don't mention the `git show` command, but you may want
  to look into this command so that you can get more detail on prior
  commits.

**Interacting with remotes**:
* What is a remote repo?
  * For instance, github is a remote repository.  But also, another folder on your computer that you have cloned from to another folder is a remote repository.
* How do you list the remote repos?
* How do you add a remote repo? (`git remote add custom_repo_name https://github.com/appacademy/example.git`)
* How do you fetch data from a remote?
* How do you push your changes to a remote?

## GitHub Keys

GitHub provides a guide to [set up your SSH keys][ssh-guide] so that
you can push your code to github. You should follow this guide so that
you may push to github from your own machine.

Normally you have one SSH key per machine; each machine you work on,
you push another SSH key to github. But we have many workstations, and
you will work at different ones every day.

Rather than setting up SSH keys on the workstations, we would ask that
you push using HTTPS.  This method will ask for your github username
and password on the command line to authorize the push, and will send
that login securely using encryption.  To use HTTPS, set the url of
the remote repository starting with `https://github.com/your_username_here/repo_name.git`
rather than `git@github.com:your_username_here/repo_name.git`.

## Commit Attribution

The next step is to configure your repo so that you are saving your
commits under the right name. This is easy, though the downside is that
each commit can only have one author. When working in a pair, pick one of
you to put initially as the commit author. Change directory into your
repo, and then run:

    git config user.name "Ned Ruggeri"
    git config user.email "ned@appacademy.io"

This will attribute all the commits to one of you. At the end of the day,
the other one from your pair can copy the repository and
[follow these instructions][git-fix-authorship] to rewrite the commits
in the copy with her/his name and email.

Make sure you do this every day! Employers will look through your github
repos when hiring!

## Additional material

We've only assigned the essential chapters about git. You should
return to Pro Git to read the following chapters on your own time:

* ch3
* ch6.1-ch6.5

## Resources
* You may want to use the AA git config files available in the
  [aa-dotfiles][aa-dotfiles] repo. At the moment these are fairly
  basic, but are a good start.
* [Pro Git][pro-git]
* How to [generate SSH keys][ssh-guide].
* A very helpful [reference][git-ref] of common git commands, targeted to
  beginners.
* [Gitready][gitready]: a blog of tips for git beginners.
* A [visual cheat-sheet][git-cheatsheet] of how git commands move files
  between workspace, index, local and upstream (remote).
* A blog post on [`git add -p`][git-add-p-post]; this lets you
  interactively add changes to files, for more granular commits.
* [Git, the Simple Guide][git-simple-guide]: A colorful summary of basic
  Git knowledge.
* A [note][commit-msgs] on writing good git commit messages.
* [Learn Git Branching][learn-git-branching]: For when you advance to
  using branches in your development workflow.
* [Git Ignore Templates][git-ignore]: A collection of `.gitignore` templates
  covering many languages and frameworks.
* [Git Immersion][git-immersion]: A longer tutorial for when you have
  some extra time.

[aa-dotfiles]: https://github.com/app-academy/aa-dotfiles
[pro-git]: http://git-scm.com/book
[ssh-guide]: https://help.github.com/articles/generating-ssh-keys
[git-ignore]: https://github.com/github/gitignore
[git-immersion]: http://gitimmersion.com/
[git-videos]: http://git-scm.com/videos
[git-ref]: http://gitref.org/
[gitready]: http://gitready.com
[git-cheatsheet]: http://www.ndpsoftware.com/git-cheatsheet.html
[git-add-p-post]: http://johnkary.net/git-add-p-the-most-powerful-git-feature-youre-not-using-yet/
[git-simple-guide]: http://rogerdudler.github.io/git-guide/
[git-tutorial]: http://www.vogella.com/articles/Git/article.html
[try-git]: http://try.github.com/
[commit-msgs]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[Branching-Strategies]: http://nvie.com/posts/a-successful-git-branching-model/
[Git Visualized]: http://www.wei-wang.com/ExplainGitWithD3/#
[learn-git-branching]: http://pcottle.github.io/learnGitBranching/?NODEMO
[git-fix-authorship]: ./git-fix-authorship.md
