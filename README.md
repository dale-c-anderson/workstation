# workstation

An Ansible playbook and cusom role which installs most of the software I use (on an Ubuntu flavored OS), to save me several hours worth of setup time on a new workstation.


## Used on
* Ubuntu 18.04
* Ubuntu 22.04
* Pop!_OS 22.04


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

3. Run the bootstrap script with sudo (you'll be installing software after all), specifying the path of the recipe to use:
   ```bash
   sudo ./bootstrap recipes/Ubuntu_22.04   # for example.
   ```
   * The bootstrap script installs ansible, downloads the contrib roles specified in `galaxy/requirements.yml`, and runs `ansible-playbook` for the recipe you chose.


## Followup

After the playbook installs software, you'll need to do the following manually:

* log in to browser profiles (chrome, firefox, etc)
* log in to cloud services (g-suite, microsoft teams, etc)
* generate new ssh keys and add them to services (github, gitlab, etc)
* add your ssh key(s) to your ssh agent
* log in to IDE profiles (jetbrains, vscode, etc)
* set up a new GPG key and configure code signing
* clone private repositories
* configure dropbox or other cloud storage services
* configure local system backups
* configure credentials for API services (aws, kubectl, docker, etc)


## Updating the contrib roles

If you ever need to re-use this playbook and you still have the repo in place, it's a good idea to update the roles first.

Sadly, Galaxy doesn't really have any facility to update roles, so the easiest way is to remove and reinstall them.

1. Purge previously downloded contrib roles,

   ```bash
   cd path/to/this/repo
   find ./roles/contrib/ -mindepth 1 -maxdepth 1 -type d | xargs rm -rfv
   ```
2. Install fresh verions,
   ```bash
   ansible-galaxy install -r ./galaxy/requirements.yml
   ```

