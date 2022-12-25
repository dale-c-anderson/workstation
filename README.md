# workstation
Install (almost) everything I need to start being productive on an Ubuntu flavored OS.


## Assumptions

I have a brand-new Ubuntu flavored OS, with absolute stock defaults.


## How to use it

1. Clone this repo:
   ```bash
   sudo apt-get install -yq git
   mkdir -pv "$HOME/repos/github.com/dale-c-anderson"
   cd "$HOME/repos/github.com/dale-c-anderson"
   git clone https://github.com/dale-c-anderson/workstation
   cd workstation
   ```

2. Have a look inside `recipes/` folder, and examine each one's `group_vars/all.yml` file. If one of them suits your needs, proceed to step 3. Otherwise, duplicate or modify one of the dirs as needed.

3. Run the bootstrap script (with sudo, you'll be installing software after all), specifying the path of the recipe to use:
   ```bash
   sudo ./bootstrap recipes/Ubuntu_22.04   # for example.
   ```
   * The bootstrap script installs ansible, installs role dependencies, and runs `ansible-playbook` for the recipe you chose.


## Followup

After the playbook installs software, you'll need to do the following manually:

* log in to browser profiles
* log in to cloud services
* generate new ssh keys and add them to services (github, gitlab, etc)
* add your ssh key(s) to your ssh agent
* log in to IDE profiles (jetbrains, vscode, etc)
* set up a new GPG key and configure code signing
* clone private repositories
* configure dropbox or other cloud storage services
