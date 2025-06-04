---
layout: default
title: Git Crash Course
parent: Coding Best Practices
---
# Git Crash Course - From Keith

## Intro

Please feel free to ignore any of my methods to the extent you need to make git work for you.  This is the workflow that I’ve landed on after many iterations and refinements, but is a good baseline for how to use git in the context of theme development.  I generally use the Source Control features in VSCode, since it’s always right there, and there’s no context change.  I will use the command line in certain situations, but in general, everything I’m likely to need to do is all done in the editor.

## How I do git

I’m very “atomic” with my commits.  By that, I mean my commits are generally very small, usually only affecting one or two files at a time.  This limits the amount of legwork needed later to figure out where something was touched.  The more you’re including in your commits, the more code you potentially have to look through to find what it is you’re looking for.  it’s also easier to write useful commit messages when you’re only dealing with a single “thing” at a time.  There’s no hard or fast rules about when and how to commit, I just prefer more small commits over a few big ones.

The VSCode addon I use for commit messages is called [VSCode Git Commit Message](https://marketplace.visualstudio.com/items?itemName=rioukkevin.vscode-git-commit).  Once installed, it will add an icon above the commit message input field that you can click to pick from different categories for your commit and write a manual commit message, and an icon in the input itself that will auto-generate a message based on the current repo changes. 

**Git Commit Message buttons**
![screenshot-2023-11-20-at-11.50.10_am.jpg](/images/screenshot-2023-11-20-at-11.50.10_am.jpg)

**Git Commit Message manual options** 
![screenshot_2023-11-20_at_11.52.38_am.png](/images/screenshot_2023-11-20_at_11.52.38_am.png)

I don’t generally use branching, but after the work we did on Alamos, I get the reasoning.  I will likely start using it going forward, but this text doesn’t include it since this is a “right now” snapshot of my workflow.

Generally, when I’m editing a file, I will commit when something “works”, based on the context.  For example, if I’m making a block that will render a group of cards, I will get it working in a bare-bones way (for example, the content shows up as expected and is in columns) and then commit.  That way, I know I can always get back to this basic layout, and start from a known-good state.  I try to limit my commits to only a single “thing”, so a single block, a single template, etc.

After I make the changes I want to commit, I flip over to the Source Control sidebar, and go through the commit process.  Usually I write manual messages, but you can use the auto-generated one if you prefer.  The key is, always make your messages relevant to what you’re pushing.  To continue the card block example, my initial message would be something along the lines of “Set up card block, no styling”.  You can view a side-by-side comparison of the changes by clicking on the file name in the Source Control view.  In the example below, I’ve removed a class I no longer need and had commented out.

**Commit message**
![screenshot_2023-11-20_at_12.58.58_pm.png](/images/screenshot_2023-11-20_at_12.58.58_pm.png)

**Working tree comparison**
![screenshot_2023-11-20_at_1.00.14_pm.png](/images/screenshot_2023-11-20_at_1.00.14_pm.png)

From there, I move on to adding styles, adding features, refactoring, etc.  Commits at this stage follow the same contextual commit pattern.  For example, say I want to add an image to the cards.  Ideally, I’d add whatever was needed to get the image on the page (ACF field call, image tag, etc), but in reality, it’s usually the image plus bits here and there within the block (header size, line-height, etc).  This still falls under my definition of “atomic” since I’m only working on a single “thing” (in this example, the card block).

Pushing is up to you.  I generally push with every commit, but you can let them stack up, push them all at once, and git will still track everything correctly (it’s not “best practice”, but in general, there’s no harm in it).  If you’re using branching, you’ll need to figure out when it’s appropriate to merge your work.  This was the one area where I didn’t follow my normal atomic methodology when working on Alamos, but that was not in any way a “normal” project.

## About History Rewriting
### Delete the last commit
Deleting the last commit is the easiest case. Let's say we have a remote origin with branch main that currently points to commit dd61ab32. We want to remove the top commit. Translated to git terminology, we want to force the main branch of the origin remote repository to the parent of dd61ab32:

`git push origin +dd61ab32^:main`

Where git interprets x^ as the parent of x and + as a forced non-fastforward push.

### Reset from a local repo
If you have the main branch checked out locally, you can also do it in two simpler steps: First reset the branch to the parent of the current commit, then force-push it to the remote.

```
git reset HEAD^ --hard
git push origin -f
```

## Other Considerations

Git is a huge topic, and this is just barely scratching the surface of how to use it.  The steps outlined above is prolly 99% of the day-to-day usage you need.  The following site is my first stop when I’m trying to figure out some of the more esoteric git use cases, but it also has some of the info covered above too: [Git Second Brain](https://blog.flotes.app/posts/git-second-brain).

Beyond that, google is your friend.  Most of the more “dangerous” git commands have dry-run versions that will show you what the command would do if you ran it for real, so if you’re nervous about trying something, I’d say to search for whichever command you want to run plus “dry run”, which should show you if a particular command has a dry-run option.  If a particular command doesn’t have that as an option, as long as you’re pushing to the remote repo, the chances of loss of work are minimized, because at worst you just pull a fresh copy from the repo and carry on.  Branching also helps with this to an extent, as if you completely trash your local branch, main should still be functional at the point of your last merge.

## Conclusion

Nothing in this document should be considered “rules”…this is simply how I use git, and it works for me.  It may work for you exactly as written, it likely will not.  Take the pieces that work for you and build your own workflow.  The key is to be consistent.