# creating a patch

https://www.debian.org/doc/manuals/maint-guide/modify.en.html#quiltrc

# Build package and create .dsc file

dpkg-source -b

# Add source package:

```
mkdir -p ~/projects/fread/apt/fread.ink_apt_mirror
cd ~/projects/fread/apt/fread.ink_apt_mirror
rsync -HPSavx juul.io:/var/www/fread.ink/public/apt 
```

cd into the directory containing the built files (including the .dsc)

To sign a package:

```
# Use the ID of the subkey for the public key shown using `gpg --list-keys`
debsign -k0D88279E mypackage.dsc
```

To add a source package:

```
reprepro -S main -b ~/projects/fread/apt/fread.ink_apt_mirror/apt includedsc enheduanna mypackge.dsc
```

To add a binary package:

```
reprepro -S main -b ~/projects/fread/apt/fread.ink_apt_mirror/apt includedeb enheduanna mypackge.deb
```


To remove a package:

```
reprepro -b ~/projects/fread/apt/fread.ink_apt_mirror/apt remove enheduanna mypackage
```

Then rsync in the other direction to put it online.


# first distro name

Enheduanna


# links

* https://wiki.debian.org/SettingUpSignedAptRepositoryWithReprepro
* http://wiki.wreiner.at/Main/OwnDebianRepository#Add_source_package


