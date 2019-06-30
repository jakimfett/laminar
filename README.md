# Laminar CI [![status](https://ci.ohwg.net/badge/laminar.svg)](https://ci.ohwg.net/jobs/laminar)

Laminar (https://laminar.ohwg.net) is a lightweight and modular Continuous Integration service for Linux. It is self-hosted and developer-friendly, eschewing a configuration UI in favour of simple version-controllable configuration files and scripts.

Laminar encourages the use of existing GNU/Linux tools such as `bash` and `cron` instead of reinventing them.

Although the status and progress front-end is very user-friendly, administering a Laminar instance requires writing shell scripts and manually editing configuration files. That being said, there is nothing esoteric here and the [guide](http://laminar.ohwg.net/docs.html) should be straightforward for anyone with even very basic Linux server administration experience.

See [the website](https://laminar.ohwg.net) and the [documentation](https://laminar.ohwg.net/docs.html) for more information.

## Building from source

First install development packages for `capnproto (version 0.7.0 or newer)`, `rapidjson`, `sqlite` and `boost` (for the header-only `multi_index_container` library) from your distribution's repository or other source. Then:

```bash
git clone https://github.com/ohwgiles/laminar.git
cd laminar
cmake .
make -j$(nproc)
sudo make install
```
Note that by default, installing with `(c)make` will overwrite your existing configuration, binary, and unit files. Make backups!

The CMakeLists.txt file sets `cmake` defaults to `CMAKE_INSTALL_PREFIX=/` and `CMAKE_BUILD_TYPE=Release`, which can be overridden with the `-DCMAKE_INSTALL_PREFIX=<path>` and `-DCMAKE_BUILD_TYPE=<type>` flags, respectively.

`make install` includes a systemd unit file. If you intend to use it, consider creating a new user `laminar` or modifying the user specified in the unit file.

