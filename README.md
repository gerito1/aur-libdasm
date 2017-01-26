AUR/libdasm
-----------
Arch Linux package based on the aur/libdasm

Here I'm using https://github.com/alexeevdv/libdasm.git repo, because google
code is down.

This package works but it will fail to make a workable install for pydasm.

Here is a patch, sadly I don't know how to properly patch git.

If you want to install libdasm  and pydasm do:

> makepkg --noarchive

Open src/libdasm/pydasm/setup.py

replace sources = ['../libdasm.c', 'pydasm.c'])

with sources = ['libdasm.c', 'pydasm/pydasm.c'])

Open PKGBUILD, and uncomment the line

  #python2 ./pydasm/setup.py install --root="$pkgdir" --optimize=1

Finally

> makepkg --repackage

And enjoy your package.
