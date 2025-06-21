# Guide: How to Manage Two GitHub Accounts on macOS

This guide walks through setting up two GitHub accounts (`trite8q1` and `gaplabshq`) on a single macOS machine. The configuration automatically selects the correct identity for commit signing (GPG) and authentication (SSH) based on the project's directory structure.

**The Goal:**
- Commits in `~/dev/trite8q1/` are signed by `trite8q1`.
- Commits in `~/dev/gaplabshq/` are signed by `gaplabshq`.
- Pushing from `~/dev/trite8q1/` authenticates as the `trite8q1` user.
- Pushing from `~/dev/gaplabshq/` authenticates as the `gaplabshq` user.
- The process is automatic after setup. No manual switching is required.

**Prerequisites:**
- [Homebrew](https://brew.sh/) installed.
- Git and GPG installed via Homebrew: `brew install git gnupg`.

### Part 1: GPG Keys for Verified Commits

First, we'll create a GPG key for each GitHub account to sign commits.

#### 1.1 Generate GPG Keys
Run the `gpg --full-generate-key` command twice, once for each account. Use the `no-reply` email address provided by GitHub in your account settings.

**For `trite8q1`:**
```sh
gpg --full-generate-key
```
- When prompted, select **(1) RSA and RSA**.
- Key size: **4096**
- Expiration: **0** (does not expire)
- Real name: `Your Name`
- Email address: `<ID>+trite8q1@users.noreply.github.com` (Find this in your GitHub email settings)

**For `gaplabshq`:**
```sh
gpg --full-generate-key
```
- When prompted, select **(1) RSA and RSA**.
- Key size: **4096**
- Expiration: **0** (does not expire)
- Real name: `Your Name`
- Email address: `<ID>+gaplabshq@users.noreply.github.com`(Find this in your GitHub email settings)

#### 1.2 List Keys and Get IDs
Find the long ID for each key you just created.

```sh
gpg --list-secret-keys --keyid-format=long
```
The output will look like this. The long key ID is the string after `rsa4096/`.
```
/Users/you/.gnupg/pubring.kbx
-----------------------------
sec   rsa4096/DDE2D324DB0EAAAA88C0E904714D074E0F99D0C6 2024-01-01 [SC]
      DDE2D324DB0EAAAA88C0E904714D074E0F99D0C6
uid                 [ultimate] Gaplabs <ID+gaplabshq@users.noreply.github.com>
ssb   rsa4096/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA 2024-01-01 [E]

sec   rsa4096/DEADBEEFDEADBEEFDEADBEEFDEADBEEFDEADBEEF 2024-01-01 [SC]
      DEADBEEFDEADBEEFDEADBEEFDEADBEEFDEADBEEF
uid                 [ultimate] Your Name <ID+trite8q1@users.noreply.github.com>
ssb   rsa4096/BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB 2024-01-01 [E]
```
Note down both long key IDs.

#### 1.3 Add GPG Keys to GitHub
Export the public part of each key and add it to the corresponding GitHub account.

```sh
# Export and copy the gaplabshq key
gpg --armor --export DDE2D324DB0EAAAA88C0E904714D074E0F99D0C6 | pbcopy

# Export and copy the trite8q1 key
gpg --armor --export DEADBEEFDEADBEEFDEADBEEFDEADBEEFDEADBEEF | pbcopy
```
- For each key, go to the correct GitHub account: **Settings** -> **SSH and GPG keys** -> **New GPG key**.
- Paste the copied key and save.

### Part 2: SSH Keys for Authentication

Next, we create separate SSH keys so `git push` can authenticate to the correct account.

#### 2.1 Generate SSH Keys
```sh
# For trite8q1
ssh-keygen -t ed25519 -f ~/.ssh/id_trite8q1 -C "<ID>+trite8q1@users.noreply.github.com"

# For gaplabshq
ssh-keygen -t ed25519 -f ~/.ssh/id_gaplabshq -C "<ID>+gaplabshq@users.noreply.github.com"
```
Press Enter to accept the default (no passphrase) for each, or enter a passphrase if you prefer. 
If it get stuck in the terminal, maybe you have to use the interactive mode, which could look like that: 
`ssh-keygen -t ed25519 -f ~/.ssh/id_trite8q1 -C "trite8q1" -N ""`

#### 2.2 Add SSH Keys to GitHub
Add the public SSH key (`.pub`) to each account.

```sh
# Copy the trite8q1 public key
pbcopy < ~/.ssh/id_trite8q1.pub
# Add it to the trite8q1 GitHub account's SSH keys.

# Copy the gaplabshq public key
pbcopy < ~/.ssh/id_gaplabshq.pub
# Add it to the gaplabshq GitHub account's SSH keys.
```

#### 2.3 Configure SSH Client
Create a `~/.ssh/config` file to tell SSH which key to use for which account.

```ini:~/.ssh/config
# trite8q1 GitHub account
Host gh-trite8q1
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_trite8q1
  IdentitiesOnly yes

# gaplabshq GitHub account
Host gh-gaplabshq
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_gaplabshq
  IdentitiesOnly yes
```
This creates two aliases, `gh-trite8q1` and `gh-gaplabshq`, that point to `github.com` but use different identity files.

### Part 3: Git Configuration for Automatic Switching

This is the core of the setup. We'll configure Git to use the correct keys and user info based on directory paths.

#### 3.1 Create Directory Structure
```sh
mkdir -p ~/dev/trite8q1
mkdir -p ~/dev/gaplabshq
```

#### 3.2 Main Git Config (`~/.gitconfig`)
This file conditionally includes other config files based on the current Git repository's path.

```ini:~/.gitconfig
[commit]
  gpgsign = true

[gpg]
  program = /opt/homebrew/bin/gpg

# If in a trite8q1 repo, load the trite8q1 config
[includeIf "gitdir:~/dev/trite8q1/"]
  path = ~/.gitconfig-trite8q1

# If in a gaplabshq repo, load the gaplabshq config
[includeIf "gitdir:~/dev/gaplabshq/"]
  path = ~/.gitconfig-gaplabshq
```

#### 3.3 Account-Specific Git Configs

**For `trite8q1` (`~/.gitconfig-trite8q1`):**
This file sets the user details and rewrites GitHub URLs to use the `gh-trite8q1` SSH alias.
```
[user]
  name = <Your Name>
  email = <ID>+trite8q1@users.noreply.github.com
  signingkey = <YOUR_TRITE8Q1_GPG_PUBLIC_KEY_ID>

[url "git@gh-trite8q1:"]
  insteadOf = git@github.com:

[url "ssh://git@gh-trite8q1/"]
  insteadOf = https://github.com/
```

**For `gaplabshq` (`~/.gitconfig-gaplabshq`):**
This file does the same for the `gaplabshq` identity.
```
[user]
  name = <Your Name>
  email = <ID>+gaplabshq@users.noreply.github.com
  signingkey = <YOUR_GAPLABSHQ_GPG_PUBLIC_KEY_ID>

[url "git@gh-gaplabshq:"]
  insteadOf = git@github.com:

[url "ssh://git@gh-gaplabshq/"]
  insteadOf = https://github.com/
```

### Part 4: Usage and Verification

Your setup is complete. It's now "set and forget."

1.  **Clone a repository**:
    Clone any repository (using either HTTPS or SSH URL) into its corresponding directory.
    ```sh
    # Example for a gaplabshq repo
    cd ~/dev/gaplabshq
    git clone https://github.com/gaplabshq/test2.git
    cd test2
    ```

2.  **Verify the configuration**:
    Inside the project, check that Git is using the right settings.
    ```sh
    # Should show the gaplabshq email
    git config user.email
    # Should show the gaplabshq GPG key
    git config user.signingkey
    ```

3.  **Commit and Push**:
    Your commits will be automatically signed, and pushes will be authenticated with the correct identity.
    ```sh
    git commit -m "My first auto-signed, auto-authenticated commit"
    git log --show-signature -1 # Verify GPG signature
    git push origin main
    ```

You're done. Repeat for any other repositories, ensuring you clone them into the directory corresponding to their GitHub owner.
