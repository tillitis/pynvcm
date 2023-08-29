# pynvcm

pynvcm with friends is a tool to program the NVCM of a Tillitis' Tkey
(ICE40).

Either clone this repository and run from the Python interpreter or
download and run our pre-packed executables from
[releases](https://github.com/tillitis/pynvcm/releases).

**Note**: programming the NVCM is non-reversiable.

**Note**: the NVCM can still be read out unless you set the security
bit.

## Usage

Set up a python virtualenv, unless if you are using the pre-packed
executables you can skip this step.

For linux
```
sudo apt install python3.10-venv
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

for macOS

```
brew install python3.10
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

for Windows
```
winget install Python.Python.3.10
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

then run with the appropriate options

```
usage: pynvcm.py [-h] [-v] [-f] [-b] [--speed SPI_SPEED] [-i] [--read READ_FILE] [--verify VERIFY_FILE] [--write WRITE_FILE] [--ignore-blank] [--secure]
                 [--my-design-is-good-enough]

options:
  -h, --help            show this help message and exit
  -v, --verbose         Show debug information and serial read/writes
  -f, --sleep_flash     Put an attached SPI flash chip in deep sleep
  -b, --boot            Deassert the reset line to allow the FPGA to boot
  --speed SPI_SPEED     SPI clock speed, in MHz
  -i, --info            Read chip ID, trim and other info
  --read READ_FILE      Read contents of NVCM
  --verify VERIFY_FILE  Verify the contents of NVCM
  --write WRITE_FILE    bitstream file to write to NVCM (warning: not reversable!)
  --ignore-blank        Proceed even if the chip is not blank
  --secure              Set security bits to prevent modification (warning: not reversable!)
  --my-design-is-good-enough
                        Enable the dangerous commands --write and --secure
```

For example to write the NVCM, verify and set the security bit use:

```
./pynvcm.py --my-design-is-good-enough --write application_fpga.bin --verify application_fpga.bin --ignore-blank --secure
```

## Licenses and SPDX tags

Unless otherwise noted, the project sources are licensed under the
terms and conditions of the "GNU General Public License v2.0 only":

> Copyright Tillitis AB.
>
> These programs are free software: you can redistribute it and/or
> modify it under the terms of the GNU General Public License as
> published by the Free Software Foundation, version 2 only.
>
> These programs are distributed in the hope that they will be useful,
> but WITHOUT ANY WARRANTY; without even the implied warranty of
> MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
> General Public License for more details.
>
> You should have received a copy of the GNU General Public License
> along with this program. If not, see:
>
> https://www.gnu.org/licenses

See [LICENSE](LICENSE) for the full GPLv2-only license text.

External source code we have imported are isolated in their own
directories. They may be released under other licenses. This is noted
with a similar `LICENSE` file in every directory containing imported
sources.

The project uses single-line references to Unique License Identifiers
as defined by the Linux Foundation's [SPDX project](https://spdx.org/)
on its own source files, but not necessarily imported files. The line
in each individual source file identifies the license applicable to
that file.

The current set of valid, predefined SPDX identifiers can be found on
the SPDX License List at:

https://spdx.org/licenses/
