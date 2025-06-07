# styx-repo

source-list local path

deb [trusted=yes] file:/path/styx-repo stable main

## Regen repo

dpkg-scanpackages pool/main /dev/null > dists/stable/main/binary-amd64/Packages

gzip -c dists/stable/main/binary-amd64/Packages > dists/stable/main/binary-amd64/Packages.gz

apt-ftparchive -c=apt-ftparchive.conf release dists/stable > dists/stable/Release

## Meta Update


cd styx-repo/linux-meta-styx

- UP verseion  in changelog
- Change version in control

dpkg-buildpackage -us -uc
mv ../*.deb ../pool/main/

- Do Regen