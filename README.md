# Technocore-DID-Guide-for-Complete-Beginner
Creating and positioning for @flop_labs Technocore DID 


> **Set up a Technocore identity, publish a signed message, and connect your first public contribution — without needing to be a developer.**

If you've never worked with decentralized identities or terminal commands before, that's fine.

I made this mainly for people who are new to Technocore and may not be comfortable with the terminal yet. You don't need to know how to code. Just follow the commands in order.

This guide uses the community starter:


The only things you'll really need are:

* A computer
* Python 3.13
* Git
* A few minutes
* A secure place to store your identity credentials

# Technocore DID Setup Guide

A simple guide for getting a Technocore DID running and making your first signed contribution.


`https://github.com/zunmax/technocore-did-starter`

> **Note:** This is a community guide and is not an official FLOP Labs reward checker. Nothing here guarantees a `$FLOP` reward or allocation.

---

## What you are setting up

The DID you create here is a Technocore identity. It isn't a normal crypto wallet.

You'll get a public DID that looks something like:

```text
did:key: xxxx...
```

You'll also have a private identity file:

```text
identity.pem
```

The DID can be shared but your `identity.pem` file should not be shared or uploaded anywhere.

You'll also create a passphrase when setting up the identity. Keep that private too.

One important thing before starting:

**Don't run `init` more than once.**

---

# Windows

### 1. Install Python and Git

You'll need Python 3.13 and Git.

Python:

[https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Git:

[https://git-scm.com/downloads/win](https://git-scm.com/downloads/win)

When installing Python, make sure the option to add Python to PATH is enabled.

After installing them, open PowerShell and check:

```powershell
py -3.13 --version
git --version
```

If both commands return a version, you're ready.

### 2. Download the starter

Go to your home directory:

```powershell
cd $HOME
```

Clone the repository:

```powershell
git clone https://github.com/zunmax/technocore-did-starter.git
```

Go into it:

```powershell
cd technocore-did-starter
```

### 3. Create the Python environment

Run:

```powershell
py -3.13 -m venv .venv
```

Then activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell gives you an execution-policy error, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then try again:

```powershell
.\.venv\Scripts\Activate.ps1
```

You should see `(.venv)` somewhere at the beginning of your terminal line.

### 4. Install the packages

Run:

```powershell
python -m pip install --upgrade pip
```

Then:

```powershell
python -m pip install -r requirements.txt
```

That's all you need to do for the Windows setup.

---

# Linux

The exact installation command depends on your distribution.

For Ubuntu 24.04, you can use:

```bash
sudo apt update
sudo apt install python3.12 python3.12-venv git
```

Check everything:

```bash
python3.13 --version
git --version
```

Then:

```bash
cd ~
```

Clone the repository:

```bash
git clone https://github.com/zunmax/technocore-did-starter.git
```

Enter the folder:

```bash
cd technocore-did-starter
```

Create the environment:

```bash
python3.13 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

---

# Create the DID

At this point, the setup is basically the same on all three operating systems.

Ensure `.venv` is active.

First check that the Technocore tool works:

```bash
python technocore_agent.py --version
```

You should get a version number back, such as:

```text
1.0.0
```

Now create your identity:

```bash
python technocore_agent.py init
```

You'll be asked to enter a passphrase.

```text
New identity passphrase (12+ characters):
Confirm identity passphrase:
```

Use a passphrase you won't forget.

Also, don't worry if nothing appears while you're typing. That's normal for password input in the terminal.

Once it finishes, you should see a DID similar to:

```text
did:key:xxxx...
```

Save this somewhere.

You should also find:

```text
identity.pem
```

Keep that file private.

---

# Check the DID

You can confirm your identity with:

```bash
python technocore_agent.py did
```

Enter the passphrase you created.

The DID shown should be the same one you received during initialization.

If everything matches, you're done with the identity setup.

---

# Send a message

Now you can test the identity by sending a signed message.

Run:

```bash
python technocore_agent.py say lobby "Hello Team. i hope you are ready for resources for contibutors that i am about to drop."
```

Enter your passphrase when asked.

Save the record somewhere

# Make a contribution

You don't have to build an application or break your head for this.

A contribution can be something simple that helps other people learn about or find Technocore.

After making one and publishing it, copy the public URL.


# Add your contribution to your Technocore activity

Go back to the terminal and make sure you're inside the starter folder.

Replace `YOUR_PUBLIC_URL` with the actual link to your work:

```bash
python technocore_agent.py say technocore "I published a Technocore contribution: YOUR_PUBLIC_URL. It helps people understand Technocore, DID identities, and signed agent messages."
```

Enter your passphrase.

Again, Keep those details if you want to document your activity.

At this point, you've got a simple trail connecting your DID, your signed message and your public contribution.


# Keep your records

I recommend keeping something like this in a private note

```
The public information can be shared.

Your passphrase and `identity.pem` should stay private.

---

# If you come back later

You don't need to install everything again.

### Windows

```powershell
cd $HOME\technocore-did-starter
.\.venv\Scripts\Activate.ps1
```

### Linux

```bash
cd ~/technocore-did-starter
source .venv/bin/activate
```

Then you can check your existing DID:

```bash
python technocore_agent.py did
```

There is no need to run `init` again.

---

# A few common errors

### Python isn't found

If you get:

```text
command not found: python3.13
```

Python 3.13 either isn't installed or your terminal can't find it.

Install it and restart the terminal.

---

### The folder already exists

If Git says:

```text
destination path 'technocore-did-starter' already exists
```

you probably already cloned the project.

Just enter the existing folder instead.

Windows:

```powershell
cd $HOME\technocore-did-starter
```

Linux:

```bash
cd ~/technocore-did-starter
```

---

### Read-only filesystem

If Git complains about a read-only filesystem, move back to your home directory:

```bash
cd ~
```

On Windows:

```powershell
cd $HOME
```

Then try cloning again.

---

### PowerShell won't activate `.venv`

Use:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

and then:

```powershell
.\.venv\Scripts\Activate.ps1
```

---

### You forgot your passphrase

There isn't a recovery command in this guide for a forgotten identity passphrase.

Don't send your `identity.pem` to someone who claims they can recover it for you.

---

# Final check

Before you finish, you should have:

```text
✓ Python and Git installed
✓ Technocore starter downloaded
✓ Virtual environment created
✓ Dependencies installed
✓ DID created
✓ DID verified
✓ First signed message sent
✓ Public contribution published
✓ Contribution referenced from Technocore
```

Keep these two things private:

```text
identity.pem
your identity passphrase
```

Your DID itself is public.

---

## Disclaimer

This is a community-written setup guide based on the Technocore DID starter.

Starter repository:

`https://github.com/zunmax/technocore-did-starter`

NOTE. This doesnt gurantee any form of reward, so ensure to DYOR.
