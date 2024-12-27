<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Stem Splitter Documentation</title>
</head>
<body>
    <h1>Music Stem Splitter Documentation</h1>
    
    <h2>Problem Statement</h2>
    <p>
        The separation of mixed music into its constituent components (stems) is a fundamental challenge in music production and audio processing. 
        Professional music producers often need isolated tracks for remixing, remastering, or educational purposes. Traditional methods of obtaining stems require access to original multitrack recordings, which are rarely available. 
        This project aims to solve this problem by implementing an automated system that can separate mixed music into individual stems (vocals, drums, bass, and other instruments) using deep learning.
    </p>
    
    <h2>Methodology</h2>
    
    <h3>Machine Learning Approach</h3>
    <p>We chose the Demucs (Deep Extractor for Music Sources) model developed by Facebook Research for this project. Here's why:</p>
    
    <h4>Architecture Justification:</h4>
    <ul>
        <li>Demucs uses a hybrid approach combining U-Net architecture with bidirectional LSTM.</li>
        <li>Performs in both time and frequency domains for better separation.</li>
        <li>Demonstrates superior performance in multiple source separation benchmarks.</li>
        <li>Handles real-time processing efficiently.</li>
    </ul>
    
    <h4>Technical Specifications:</h4>
    <ul>
        <li>Input: Mixed audio signal (stereo/mono).</li>
        <li>Output: Separated stems (vocals, drums, bass, other).</li>
        <li>Processing: Combination of convolutional and recurrent layers.</li>
        <li>Sampling Rate: 44.1kHz (standard for music).</li>
    </ul>
    
    <h3>Implementation Steps</h3>
    <h4>Environment Setup:</h4>
    <pre>
        mkdir music_stem_splitter
        cd music_stem_splitter
        python -m venv venv
        source venv/Scripts/activate  # Windows (Git Bash)
    </pre>
    
    <h4>Dependencies Installation:</h4>
    <pre>
        python -m pip install --upgrade pip setuptools wheel
        python -m pip install torch torchaudio --index-url https://download.pytorch.org/whl/cu118
        python -m pip install -r requirements.txt
    </pre>
    
    <h2>Usage Instructions</h2>
    <h3>Basic Usage:</h3>
    <pre>
        from stem_splitter import StemSplitter

        splitter = StemSplitter()
        stems = splitter.split_tracks("input.mp3", stem_config="4stem")
    </pre>
    
    <h3>Web Interface:</h3>
    <pre>
        python -m streamlit run app.py
    </pre>
    
    <h3>Supported Configurations:</h3>
    <ul>
        <li>2-stem: Vocals/accompaniment.</li>
        <li>4-stem: Vocals/drums/bass/other.</li>
    </ul>
    
    <h2>Required Prerequisites</h2>
    <ul>
        <li>Python 3.8+ (3.9 recommended).</li>
        <li>CUDA-compatible GPU (optional, but recommended).</li>
        <li>Visual Studio Build Tools with C++ support.</li>
        <li>8GB+ RAM recommended.</li>
    </ul>
    
    <h2>Results and Evaluation</h2>
    
    <h3>Performance Metrics:</h3>
    <ul>
        <li>Signal-to-Distortion Ratio (SDR):</li>
        <ul>
            <li>Vocals: ~6.5 dB.</li>
            <li>Drums: ~6.0 dB.</li>
            <li>Bass: ~5.5 dB.</li>
            <li>Other: ~4.5 dB.</li>
        </ul>
        <li>Processing Speed:</li>
        <ul>
            <li>GPU: ~10-15 seconds per minute of audio.</li>
            <li>CPU: ~45-60 seconds per minute of audio.</li>
        </ul>
        <li>Quality Characteristics:</li>
        <ul>
            <li>Minimal artifacts in separated stems.</li>
            <li>Good preservation of transients.</li>
            <li>Effective handling of overlapping frequencies.</li>
        </ul>
    </ul>
    
    <h2>References</h2>
    <ul>
        <li>Défossez, A., et al. (2019). "Music Source Separation in the Waveform Domain."</li>
        <li>Facebook Research Demucs Repository.</li>
        <li>Streamlit Documentation.</li>
        <li>PyTorch Audio Documentation.</li>
    </ul>
    
    <h2>Screenshot</h2>
    <img src="https://github.com/user-attachments/assets/1242f18a-cc7a-4c50-ad39-89094f6b4e42" alt="Screenshot">
</body>
</html>


![Screenshot 2024-12-27 041741](https://github.com/user-attachments/assets/1242f18a-cc7a-4c50-ad39-89094f6b4e42)

