Repositories are centralized locations where software packages are stored, managed, and made available for installation, upgrades and uninstallation.
Main configurations of lists of software are located in /etc/apt/sources.list in Debian systems.
Debian packages are named like `name_version_buildNumber_architecutre.deb`.

#### Adding configuration to sources.list
The recommended method is to create **new files within the** **/etc/apt/sources.list.d/** **directory** (e.g., `azim.sources.list`). These files are automatically included by the package manager, making management cleaner and more modular.

#### Update the config list, not actually upgrade the softwares
`sudo apt-get update`

`/var/cache/apt/` - contains cached information about local cache of repository

Packages are often organized into **categories** (e.g., `main`, `restricted`, `contrib`, `universe`).

    ◦ `main` typically includes core free and open-source software.

    ◦ `restricted` might include software with legal restrictions or closed-source components

Links: [[Package Manager in Linux]] [[Debian package manager commands]]]

202509101339

