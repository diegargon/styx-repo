# styx-repo

source-list local path

deb [trusted=yes] file:/path/styx-repo stable main

## Regen

dpkg-scanpackages pool/main /dev/null > dists/stable/main/binary-amd64/Packages

gzip -c dists/stable/main/binary-amd64/Packages > dists/stable/main/binary-amd64/Packages.gz

apt-ftparchive -c=apt-ftparchive.conf release dists/stable > dists/stable/Release