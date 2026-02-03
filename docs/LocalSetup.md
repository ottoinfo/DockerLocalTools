### [⬅ Back](../README.md)

### Setup Project

**Prefer using `$HOME` over `~`. So make sure you have this as a ENV in your terminal.

- Check $HOME env
```
# Paste and Run in Terminal
echo $HOME
```

- Create Project Folder
```
# Paste and Run in Terminal
mkdir $HOME/Docker
cd $HOME/Docker
```

- Clone the REPO
```
# Paste and Run in Terminal
git clone git@github.com:ottoinfo/DockerLocalTools.git LocalTools
```

### Brew Update/Upgrade

**Optional:** I did not want to add `brew update && brew upgrade` into setup scripts. Developers should have the option to decide if they want to update/upgrade.

Brew will sometimes have notes for adding code to files or you need to run a script.

We do have a script ( `scripts/brewCheck.sh` ), if we ever want to add into the flow, but Developers should choose.

```code
# Paste and Run in Terminal
brew update && brew upgrade

// You can also check your system is working correctly
brew doctor
```

### Run setup

> We Will have a script that should install everything for you, but lets keep track if something goes wrong. Where did it go wrong? Please report issues.

**NOTE:** You should be prompted on each step, we will check if things exist else we will prompt the developer to install/setup certain apps/features. Somethings are optional so please read the Terminal messages.

```code
# Paste and Run in Terminal
cd $HOME/Docker/LocalTools
./scripts/setup.sh
```

What should happen:
- [ ] download brew
- [ ] upgrade bash ( if you did not )
- [ ] brew install --cask orbstack


### Different Scripts

Want to make a way to create scripts for different features or setups.

```code
# Paste and Run in Terminal
./scripts/choose.sh
```

This will prompt the user through options of scripts the user can run

scriptList=(setup newMachine brew githubTokens sslCerts hosts bashUpgrade )

| Option | Description |
| ----------- | ----------- |
| 1 | Start Services: creates images, creates container, and will start all services
| 2 | Stop Services: safely stop all docker services
| 3 | Kill Services: stops all services and will remove container
| 4 | Initial Setup: this will prompt you through scripts and get your local machine running
| 5 | New Machine: this will prompt you with common brew commands and applications you may want to use
| 6 | Orb Stack: Docker replacement, install the application
| 7 | Quit
