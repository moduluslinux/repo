# Blocks Repositories
These are the repositories for the Blocks Package Manager and Modulus Linux. They are aimed at giving a massive choice of software while not restricting anyone to any rules of the program being installed in spirit of Modulus. This means that the init can be changed, the compiler can be changed, the kernel can be changed, and anything can be added, removed, or even prevented. Modulus gives you the choice to do so with a large selection of software. Although the repositories are currently small, feel free to make a package and contribute using the following guide.

## Creating a package for Blocks
A Blocks package is a folder consisting of text files and shell scripts to install and identify the package. The most bare package base is consisting of two files named `blx@add` and `blx@remove`. On a Blocks package in this repository (and also for the `get` command to work), you will also need the `blx@get` file, but it is optional on external packages. The following will explain the required and optional files in a package, both external and in the repository. It is also recommended to look at each individual package to get a feel for the formatting.

### Needed files in a package
These are needed for installing the package, and must be marked as executable.
* `blx@get` is for downloading the files needed for the package and doing other minor tasks, such as extracting the archive containing the software. 
* `blx@add` is for everything else while installing a package; installing and compiling the software included.
* `blx@remove` is for removing the package, which includes not only removing it from the system, but also removing what might have been downloaded with `get`.
* `blx@delete` is for removing all of the configuration and leftover files of the package and cleaning it out in order to completely make sure it is off the system. This is also an optional command in case the package does not use a configuration or similar files of sorts.

### Optional files in a package
These aren't scripts, but rather mere text files that include information about the package.
* `blx@depends` is what contains the needed dependencies, seperated by line breaks. If one of them is banned on the system which it is being installed on, it will skip the dependency. If there is no such file, it will be assumed that there are no dependencies.
* `blx@version` is the version of the package, which will be needed for the software to be updated. It is optional, but doing without it will prevent updates from being installed automatically.
* `blx@author` is the name of the organization, author or maintainer for identification purposes.
* `blx@description` is the description of the package for identification purposes, which should be brief, but isn't limited to.
* `blx@tags` is what contains the tags of the package, seperated by line breaks. These are used to easily identify the package, but can also be used for banning packages in bulk, preventing it from being installed on that specific system.

## Guidelines for Blocks Repositories
Please keep harmful files out, even if it is intentional and or satire. The `blx@remove` script must remove all files of a package that deem it operational, and the `blx@delete` script should delete the rest of the files, minus the files that came with the standalone package. Do not store entire tarballs or sources inside of the repositories, rather use the `blx@get` script to download the files automatically (this is why it is a requirement on downloading from the repositories). There is no style guide for how the packages should be built and how the scripts should be formatted, but try to keep it clean and understandable if possible, and try not to intentionally limit the package from being installed on a certain system.
