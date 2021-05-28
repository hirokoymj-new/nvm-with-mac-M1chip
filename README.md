# Installation nvm on macOS Big Sur with M1chip

### 1. Delete all node in your mac completely.

1. Go to `/usr/local/lib` and delete any **node** and **node_modules**.

```js
cd /usr/local/lib && ls -la
sudo rm -rf node*
```

2. Go to `/usr/local/include` and delete any **node** and **node_modules**.

```js
cd /usr/local/include && ls -la
sudo rm -rf node*
```

3. Go your home directory. `cd ~`. Check for any "local" or "lib" or "include" folders, and delete any "node" or "node_modules" from there.

4. Go to `/usr/local/bin` and delete any **node** executable

```js
cd /usr/local/bin && ls -la
sudo rm -rf node*
```

### 2. Use following url and run on terminal.

- you are using the zsh shell

```js
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | zsh
```

### 3. After installing nvm, install the latest node.

```js
nvm install node
```

### [IMPORTANT!!]4. Install any node version that you need. 

```js
# Check what version you're running:
$ node --version
v14.15.4
# Check architecture of the `node` binary:
$ node -p process.arch
arm64
# This confirms that the arch is for the M1 chip, which is causing the problems.
# So we need to uninstall it.
# We can't uninstall the version we are currently using, so switch to another version:
$ nvm install v12.20.1
# Now uninstall the version we want to replace:
$ nvm uninstall v14.15.4
# Launch a new zsh process under the 64-bit X86 architecture:
$ arch -x86_64 zsh
# Install node using nvm. This should download the precompiled x64 binary:
$ nvm install v14.15.4
# Now check that the architecture is correct:
$ node -p process.arch
x64
# It is now safe to return to the arm64 zsh process:
$ exit
# We're back to a native shell:
$ arch
arm64
# And the new version is now available to use:
$ nvm use v14.15.4
Now using node v14.15.4 (npm v6.14.10)
```
