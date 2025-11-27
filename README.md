# Beethoven Symphony No. 7 - 3D Orchestral Visualization

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)

An interactive 3D visualization that maps Beethoven's Symphony No. 7 as spatial architecture, using real orchestral score data to create a unique audio-visual experience.


## ✨ Features

- **Real Orchestral Score Data** - Parsed from actual Beethoven sheet music (MusicJSON format)
- **Progressive Reveal** - Notes appear exactly when they're played in the symphony
- **Color-Coded Instruments** - Visual separation of strings, woodwinds, brass, and percussion
- **Dynamic Synchronization** - Real-time audio-visual sync
- **Interactive 3D Controls** - Rotate, zoom, and explore the musical space
- **Spatial Time Mapping** - Distance from origin represents temporal progression
- **Transition Visualization** - Bold lines for fast passages, dotted lines for sustained notes

## 🎨 Concept

This visualization treats music as **spatial architecture**, positioning each note in 3D space based on:

- **Radial distance** = Time (0:00 at center → end at outer edge)
- **Angular position** = Pitch (MIDI note number)
- **Vertical position** = Octave + instrument family region
- **Color** = Instrument family (Blue/Yellow/Green/Red)
- **Brightness** = Dynamics (pp → ff)
- **Size** = Dynamic intensity (larger = softer, smaller = louder)
- **Line style** = Transition speed (solid = fast, dotted = slow)

## 🚀 Quick Start

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, or Edge)
- No installation required!

### Running Locally

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/beethoven-symphony-3d.git
cd beethoven-symphony-3d
```

2. **Ensure all files are in the same directory**
   - `beethoven_symphony_real_score.html`
   - `beethoven_symphony_7_mvt1__2_.json`
   - `beethoven_symphony_7.mp3`

3. **Open the HTML file**
```bash
# On Mac
open beethoven_symphony_real_score.html

# On Linux
xdg-open beethoven_symphony_real_score.html

# On Windows
start beethoven_symphony_real_score.html
```

4. **Press Play** and watch the visualization!

### Using a Local Server (Recommended)

```bash
# Python 3
python -m http.server 8000

# Then open: http://localhost:8000/beethoven_symphony_real_score.html
```


## 🎮 Controls

### Mouse Controls
- **Left-click + Drag** - Rotate the 3D space
- **Scroll** - Zoom in/out
- **Right-click + Drag** - Pan the view

### Playback Controls
- **Play/Pause** - Start/stop the symphony
- **Restart** - Return to beginning
- **Toggle Checkboxes** - Show/hide instrument families

## 🎯 Technical Details

### Technologies Used
- **Three.js** (r128) - 3D rendering engine
- **Web Audio API** - Audio playback and synchronization
- **Vanilla JavaScript** - No frameworks required
- **HTML5 Canvas** - High-performance rendering

### Data Format
The orchestral score uses **MusicJSON** format containing:
- 11 orchestral parts (Flutes, Oboes, Clarinets, Bassoons, Horns, Trumpets, Timpani, Violin I, Violin II, Viola, Cello/Bass)
- Tempo markings (Poco sostenuto 69 BPM → Vivace 104 BPM)
- Exact pitch, duration, dynamic, and articulation for each note

### Spatial Mapping Algorithm

```javascript
For each note in the score:
  1. Calculate real time from tempo + beat position
     time = measureStart + (beat × secondsPerBeat)
  
  2. Map to radial position
     radius = (noteTime / totalDuration) × maxRadius
  
  3. Map to angular position
     angle = (midiPitch / 127) × 360°
  
  4. Add instrument family offset
  
  5. Calculate 3D coordinates:
     x = radius × cos(angle) + familyOffset.x
     y = octaveHeight + familyOffset.y
     z = radius × sin(angle) + familyOffset.z
```

## 📊 Instrument Families

| Family | Color | Notes | Spatial Region |
|--------|-------|-------|----------------|
| **Strings** | 🔵 Blue | 22 | Lower-left (foundation) |
| **Woodwinds** | 💛 Yellow | 16 | Upper-right (melodic) |
| **Brass** | 💚 Green | 4 | Central-right (power) |
| **Percussion** | 🔴 Red | 3 | Center-bottom (rhythm) |


