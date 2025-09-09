
# flashberry

[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)](https://unlicense.org/)
![Shell Script](https://img.shields.io/badge/language-Bash-green.svg)
![Platform](https://img.shields.io/badge/platform-Linux-lightgrey.svg)


<img width="50%" alt="project image" src="https://github.com/user-attachments/assets/263e7472-3e61-4425-93c9-0bba7658712b" />

**flashberry** is a simple shell script for flashing (optionally compressed) disk images directly onto block devices.  

It exists because I kept having to look up the `dd` command line (especially the part with `oflag=direct`), and various flags for the decompressors - so I wrote a wrapper that handles the messy parts, supports common compression formats, and adds a few safety checks.

---

## Features

- Supports `.img`, `.gz`, `.xz`, `.bz2`, `.zst`, and `.zip` (single-file) images.
- Verifies target device, checks for mounted/system disks, and asks for confirmation when needed.
- Uses `pv` for progress reporting.
- Streams directly: no need to decompress to disk first.
- Just one file, no dependencies beyond standard Linux tools.

---

## Installation

Clone or download the script, then:

```bash
chmod +x flashberry
````

Optionally copy it into a directory on your `$PATH` (e.g., `/usr/local/bin`):

```bash
sudo cp flashberry /usr/local/bin/
```

---

## Usage

```bash
flashberry /path/to/file.img.xz /dev/sdX
```

Where:

* `/path/to/file.img.xz` is the compressed or raw disk image.
* `/dev/sdX` is the block device you want to overwrite.

---

## ⚠️ Warning

This script **writes directly to block devices**. 
> If you point it at the wrong disk, you can absolutely overwrite important data, your operating system, or your collection of pictures of your favorite dog doing tricks. If that happens, I am sorry for you, **but am in no way responsible**.

**Standard disclaimer:**
> This software is provided *as-is*, without warranty of any kind. Use at your own risk. The author assumes no liability for data loss, hardware damage, or general mayhem caused by misuse.

---

## License

This project is released into the public domain under the [Unlicense](https://unlicense.org/).
You are free to copy, modify, distribute, and use it for any purpose without restriction.

---

## Notes

* This project has nothing to do with marijuana. I don’t support its use.
* “flashberry” is just a name; think of SD cards, Raspberry Pis, and flashing images.
