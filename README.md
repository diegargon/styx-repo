# styx-repo

> ⚠️ **Nota:** GitHub no puede usarse directamente como repositorio APT porque no sirve los archivos ni las cabeceras HTTP que espera APT.
> Para usar este repo, debes:
> - Servirlo con GitHub Pages (ejemplo: `https://diegargon.github.io/styx-repo`)
> - O clonar el repo localmente y usar `deb [trusted=yes] file:/ruta/al/styx-repo stable main` en tu sources.list

deb [trusted=yes] https://github.com/diegargon/styx-repo stable main

## Regen

dpkg-scanpackages pool/main /dev/null > dists/stable/main/binary-amd64/Packages

gzip -c dists/stable/main/binary-amd64/Packages > dists/stable/main/binary-amd64/Packages.gz

apt-ftparchive release dists/stable > dists/stable/Release

## Problemas comunes

- **Permiso denegado (`Permiso denegado` o `couldn't be accessed by user '_apt'`):**
  Da permisos de lectura a todo el repo:
  ```sh
  sudo chmod -R a+rX /root/styx-repo
  ```

- **Distribución conflictiva:**
  Asegúrate de que el archivo `dists/stable/Release` contiene las líneas correctas:
  ```
  Suite: stable
  Codename: bookworm
  ```
  Y que no hay líneas vacías al principio del archivo.
