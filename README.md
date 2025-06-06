# styx-repo

deb [trusted=yes] https://github.com/diegargon/styx-repo stable main

dpkg-scanpackages pool/main /dev/null > dists/stable/main/binary-amd64/Packages

gzip -c dists/stable/main/binary-amd64/Packages > dists/stable/main/binary-amd64/Packages.gz

apt-ftparchive release dists/stable > dists/stable/Release
