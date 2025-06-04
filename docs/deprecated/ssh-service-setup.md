---
layout: default
title: SSH Service Setup
parent: Flywheel
grand_parent: Deprecated
---

# Install LocalWP

Go to [LocalWP](https://localwp.com/) and click on the green Download Now button.  Platform will be “Mac Apple Silicon”.  Fill out the form, and download.  Install after it finishes.

## SSH Keys & Configuration

Most of the following steps will be done in terminal. The screenshots below will look slightly different since my terminal is customized, but the command output should be the same.

Generate an ed25519 SSH key using the following command (changing the email address to your email):

```plaintext
ssh-keygen -t ed25519 -C "your_email@vincentdesign.ca"
```

You should see output that looks like the following. Hit enter to accept the default file name, or give it a specific name.  The key here is to remember this name so we can use it later.

![](/images/screenshot_2023-06-20_at_10.20.55_am.png)

It will now ask you for a passphrase, LEAVE THIS BLANK.  Just hit enter here twice.

![](/images/screenshot_2023-06-20_at_10.25.04_am.png)

(note, I changed my key name because I already have a key with the default name)

The generator will spit out some info about your key, but it’s nothing that you need to keep track of.  Now, you need to start the SSH agent using the following command:

```plaintext
eval "$(ssh-agent -s)"
```

You should see something like the following.  The number will be different, but as long as it doesn’t return an error, it’s fine.

![](/images/screenshot_2023-06-20_at_10.30.00_am.png)

Now we need to tell the agent to load your keys automatically.  To do this, we need to add the following to the SSH config file.  Open the file with the following commands:

```plaintext
touch ~/.ssh/config
nano ~/.ssh/config
```

In the file, add the following, changing the filename if you gave it a different name:

```plaintext
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

It should look like this when you’re done:

![](/images/screenshot_2023-06-20_at_10.37.21_am.png)

Press ctrl-X, press Y to save and accept the default filename when asked.  You’re now ready to add your key to Flywheel.  We will handle adding the key to GitHub in the next guide. Before we start, copy your public key to the clipboard using the `pbcopy` command.  It will not generate any output, but your key is ready to paste in the steps below:

![](/images/ssh-key-copy.png)

## Add key to Flywheel

Log into your Flywheel account, and click on your icon in the upper-right corner.  Select Account from the dropdown.

![](/images/screenshot_2023-06-20_at_10.59.06_am.png)

On the Account page, click on the SSH tab, then click the Add SSH Key button.

![](/images/screenshot_2023-06-20_at_11-02-14_flywheel.png)

Similar to WPEngine, fill in the form, and click the Add Key button to save your key.

![](/images/screenshot_2023-06-20_at_11-04-10_flywheel.png)