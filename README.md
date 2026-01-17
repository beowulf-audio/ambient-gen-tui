# 🎼 Ambient Generator TUI

Create lush, generative ambient music with spacey textures in your terminal.

## Features

- 🎼 **Multiple scales** - Currently featuring Japanese pentatonic scales (Hirajoshi, In Sen, Kumoi, Yo)
- 🎹 **Five layered instruments** (Pad, Flute, Vibraphone, Strings, Music Box)
- 🎚️ **Adjustable tempo and length**
- 🎨 **Multiple soundfonts** (5 high-quality GM soundfonts included)
- 🎛️ **Audio effects** (Reverb and Paulstretch time-stretching)
- 📦 **Export to MIDI, WAV, and MP3**
- 💻 **Beautiful terminal user interface** (TUI)
- ⚡ **Zero system dependencies** - just `pip install` and go!

## Installation

```bash
pip install ambient-gen
```

That's it! All dependencies (including soundfonts and FFmpeg) are automatically installed. Works on macOS, Linux, and Windows with no additional setup required!

## Quick Start

Launch the interactive TUI:

```bash
ambient-gen
```

Or generate a track with default settings:

```bash
ambient-gen --quick
```

## Usage

### Interactive Mode

```bash
ambient-gen
```

#### Keyboard Controls

**Generation & Files:**
- `g` - Generate new track (creates MIDI, WAV, and MP3)
- `o` - Open output folder
- `q` - Quit

**Scale Selection:**
- `s` - Cycle through scales (Hirajoshi → In Sen → Kumoi → Yo)

**Parameters:**
- `↑/k` or `↓/j` - Adjust tempo (30-120 BPM)
- `→/l` or `←/h` - Adjust length (4-32 bars)

**Instruments:**
- `1` - Toggle Pad layer
- `2` - Toggle Flute layer
- `3` - Toggle Vibraphone layer
- `4` - Toggle Strings layer
- `5` - Toggle Music Box layer

**Audio Options:**
- `a` - Toggle audio effects (Reverb + Paulstretch)
- `e` - Toggle effects only mode (just reverb/paulstretch, no dry signal)
- `f` - Cycle soundfonts (FluidR3 GM, GeneralUser, MS Basic, SGM, Timbres of Heaven)
- `p` - Toggle Paulstretch time-stretching effect

**Visual:**
- `Ctrl+P` - Change color palette

### Command Line Mode

Generate without the TUI:

```bash
# Quick generation with defaults
ambient-gen --quick

# Specify scale
ambient-gen --quick --scale hirajoshi

# Custom tempo and length
ambient-gen --quick --tempo 60 --bars 16

# With audio effects
ambient-gen --quick --effects
```

### Output Files

Generated files are saved to `~/Desktop/ambient_gen_output/`:
- `ambient_YYYYMMDD_HHMMSS.mid` - MIDI file
- `ambient_YYYYMMDD_HHMMSS.wav` - High-quality WAV audio (44.1kHz, 16-bit)
- `ambient_YYYYMMDD_HHMMSS.mp3` - Compressed MP3 audio (192kbps)

## How It Works

1. **Generates MIDI**: Creates generative compositions using Japanese pentatonic scales with intelligent note placement and dynamics
2. **Renders Audio**: Uses tinysoundfont to synthesize audio with high-quality GM soundfonts (automatically extracted on first run)
3. **Applies Effects**: Optional reverb and Paulstretch time-stretching for ambient textures
4. **Converts to MP3**: Automatically uses FFmpeg (via static-ffmpeg) to create compressed audio

All of this happens automatically with zero configuration!

## Japanese Scales

- **Hirajoshi** (平調子): Traditional pentatonic scale (0, 2, 3, 7, 8) - Contemplative and meditative
- **In Sen** (陰旋): Mystical and contemplative (0, 1, 5, 7, 10) - Dark and mysterious
- **Kumoi** (雲井): Bright and ethereal (0, 2, 3, 7, 9) - Light and floating
- **Yo** (陽): Simple and peaceful (0, 2, 5, 7, 9) - Major pentatonic, uplifting

## Included Soundfonts

The package includes 5 high-quality General MIDI soundfonts (compressed to 120MB):

- **FluidR3 GM** (23MB) - Clean, balanced GM soundfont
- **GeneralUser GS** (7MB) - Excellent pads and flutes, great for ambient
- **MS Basic** (49MB) - MuseScore's default soundfont
- **SGM V2.01** (27MB) - Rich, warm ambient tones
- **Timbres of Heaven** (51MB) - Huge GM/GS/XG soundfont with extensive samples

Soundfonts are automatically extracted from a compressed archive on first import.

## Development

### Install in Development Mode

```bash
git clone https://github.com/yourusername/ambient-gen.git
cd ambient-gen
pip install -e .
```

### Project Structure

```
ambient_gen/
├── __init__.py              # Package init with soundfont extraction
├── __main__.py              # Entry point for python -m
├── tui.py                   # Main TUI application
├── midi_generator.py        # MIDI composition engine
├── audio_renderer.py        # Audio synthesis and effects
├── soundfont_manager.py     # Soundfont discovery and management
└── soundfonts.tar.xz        # Compressed soundfonts (120MB)
    → Extracts to soundfonts/ on first import
```

## Technical Details

- **Audio Quality**: 44.1kHz, 16-bit stereo WAV
- **MIDI Resolution**: 960 ticks per quarter note
- **Effects**: Freeverb reverb, Paulstretch time-stretching (4x stretch)
- **Package Size**: ~120MB (soundfonts compressed with xz)
- **Python Version**: 3.8+

## Credits

- **Soundfonts**:
  - [FluidR3 GM](https://github.com/musescore/MuseScore/tree/master/share/sound) - Frank Wen
  - [GeneralUser GS](https://schristiancollins.com/generaluser.php) - S. Christian Collins
  - [MS Basic](https://musescore.org/) - MuseScore
  - [SGM V2.01](https://archive.org/details/SGM-V2.01) - Shan
  - [Timbres of Heaven](http://www.midkar.com/soundfonts/) - Don Allen
- **Audio Synthesis**: [tinysoundfont](https://github.com/nwhitehead/tinysoundfont-pybind)
- **FFmpeg Integration**: [static-ffmpeg](https://github.com/zackees/static_ffmpeg)
- **TUI Framework**: [Textual](https://textual.textualize.io/)

## License

MIT License - see LICENSE file for details.
