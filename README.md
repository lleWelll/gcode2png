# gcode2png

python3 script for 3D rendering gcode files with [Mayavi](https://docs.enthought.com/mayavi/mayavi/)

## Features

- `--help` is showing usage
- different options to show bed, model  + moves + supports
- auto adjust camera based on the model dimensions and location
- remove first 5 gcode entries from object - helps not to show pruge lines,
  which would distract the camera view etc
- option to define output image resolution
- option to show image preview (no more weird unrendered windows)
- set env var `LOGLEVEL=DEBUG` to see log flood on stderr
- python 3.10+

## Examples

Good examples:

![tests/1.512.png](tests/1.512.png)
![tests/2.512.png](tests/2.512.png)
![tests/hana_swimsuit_fv_solid_v1.512.png](tests/hana_swimsuit_fv_solid_v1.512.png)
![tests/skullbowl_0.4n_0.2mm_PETG_MINI_17h6m.512.png](tests/skullbowl_0.4n_0.2mm_PETG_MINI_17h6m.512.png)

Not so great examples:

![tests/crystal.512.png](tests/crystal.512.png)
![tests/tension-meter_petg_mini.512.png](tests/tension-meter_petg_mini.512.png)
![tests/test_nano.512.png](tests/test_nano.512.png)

## Known limitations

- python 3.10+
- tested under Ubuntu 22.04, and nothing else
- no longer compatible with forked projects
- some gcode files are rendered weird, see `test_nano.gcode`, for example I have
  some custom gcode to trigger photos for timelapse, and thus some renders
  contain those lines that go to the back of the plate and then to the right -
  this is especially visible in `skullbowl`, `crystal` and `test_nano` examples
- no support for bgcode
- no support for absolute moves in gcode

## Requirements

Tested under Ubuntu 22.04

```shell
suto apt install -y mayavi
pip3 install -r requirements.txt
```

## Usage

```shell
python ./gcode2png.py --help
```

## Develop

```shell
make clean
make -j12 all
make -j12 previews previews_md
```

## Thanks

- initial gcode2png idea forked from [Zst](https://github.com/Zst/gcode2png),
  which was forked from [shodushi](https://github.com/shodushi/gcode2png)
- [gcodeParser.py](https://github.com/jonathanwin/yagv)

## Todo

- add thumbnail generations for Linux
- add install to makefile
