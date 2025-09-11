- apt-get install `package-name` - download and installs the package
- apt-get -s `package-name` - simulates the installation
- apt-get --download-only `package-name` - only downloads, but not installs the package
- apt-get remove `package-name` - remove exact package
	- apt-get autoremove `package-name` - removes also dependent packages
- apt-cache search `string` - whatever package contains a string
- apt-get install -f - fix dependent packages and install all required packages
- dpkg -I(capital i) `package-name` - information about the package
	- apt-get info - does the same thing 
- dpkg -l - all installed packages
- dpkg-reconfigure `pakcage-name` - runs configuration setup for the package

Links:

202509102139

