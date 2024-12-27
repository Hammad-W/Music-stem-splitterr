# Music-stem-splitterr
<h1>Music Stem Splitter Documentation<h1></h1>
<h2>Problem Statement</h2>
<p>The separation of mixed music into its constituent components (stems) is a fundamental challenge in music production and audio processing. Professional music producers often need isolated tracks for remixing, remastering, or educational purposes. Traditional methods of obtaining stems require access to original multitrack recordings, which are rarely available. This project aims to solve this problem by implementing an automated system that can separate mixed music into individual stems (vocals, drums, bass, and other instruments) using deep learning.</p>
<h2>Methodology</h2>
<h3>Machine Learning Approach</h3>
  
We chose the Demucs (Deep Extractor for Music Sources) model developed by Facebook Research for this project. Here's why:

<li>
  <ol>>Architecture Justification:</ol
<ul>Demucs uses a hybrid approach combining U-Net architecture with bidirectional LSTM.</ul>
<ul>Performs in both time and frequency domains for better separation.</ul>
<ul>Demonstrates superior performance in multiple source separation benchmarks.</ul>
<ul>Handles real-time processing efficiently.
  </li>
Technical Specifications:
Input: Mixed audio signal (stereo/mono).
Output: Separated stems (vocals, drums, bass, other).
Processing: Combination of convolutional and recurrent layers.
Sampling Rate: 44.1kHz (standard for music).
Implementation Steps
Environment Setup:
mkdir music_stem_splitter
cd music_stem_splitter
python -m venv venv
source venv/Scripts/activate  # Windows (Git Bash)
Dependencies Installation:
python -m pip install --upgrade pip setuptools wheel
python -m pip install torch torchaudio --index-url https://download.pytorch.org/whl/cu118
python -m pip install -r requirements.txt

Usage Instructions
Basic Usage:
from stem_splitter import StemSplitter

splitter = StemSplitter()
stems = splitter.split_tracks("input.mp3", stem_config="4stem")
Web Interface:
python -m streamlit run app.py
Supported Configurations:
2-stem: Vocals/accompaniment.
4-stem: Vocals/drums/bass/other.

Required Prerequisites:
Python 3.8+ (3.9 recommended).
CUDA-compatible GPU (optional, but recommended).
Visual Studio Build Tools with C++ support.
8GB+ RAM recommended.
Results and Evaluation
Performance Metrics
Signal-to-Distortion Ratio (SDR):
Vocals: ~6.5 dB.
Drums: ~6.0 dB.
Bass: ~5.5 dB.
Other: ~4.5 dB.
Processing Speed:
GPU: ~10-15 seconds per minute of audio.
CPU: ~45-60 seconds per minute of audio.
Quality Characteristics:
Minimal artifacts in separated stems.
Good preservation of transients.
Effective handling of overlapping frequencies.


References
Défossez, A., et al. (2019). "Music Source Separation in the Waveform Domain."
Facebook Research Demucs Repository.
Streamlit Documentation.
PyTorch Audio Documentation.


![Screenshot 2024-12-27 041741](https://github.com/user-attachments/assets/1242f18a-cc7a-4c50-ad39-89094f6b4e42)

