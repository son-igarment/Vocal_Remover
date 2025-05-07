# Vocal Remover

*Developed by Phạm Lê Ngọc Sơn*

## Overview

Vocal Remover is an audio processing tool designed to isolate or remove vocals from music tracks, allowing users to create instrumental versions or karaoke tracks. It leverages advanced AI-powered spectral analysis to separate vocal elements from background music with precision.

## Project Structure

```
Vocal_Remover/
├── .git/                   # Git repository files
├── .gitignore              # Git ignore configuration
├── LICENSE                 # License file
├── README.md               # This file
├── requirements.txt        # Python dependencies
├── appendix/               # Additional resources
├── models/                 # Pre-trained model storage
├── lib/                    # Core library code
│   ├── __init__.py
│   ├── dataset.py          # Dataset handling utilities
│   ├── layers.py           # Neural network layers
│   ├── nets.py             # Neural network architecture
│   ├── spec_utils.py       # Spectrogram utilities
│   ├── utils.py            # General utilities
├── train.py                # Training script
├── inference.py            # Inference script for audio separation
├── augment.py              # Data augmentation script
└── pseudo.py               # Pseudo-label generation script
```

## Features

- Separate vocals from instrumental music
- High-quality spectral processing
- Trained on diverse music datasets
- Supports multiple input formats
- Command-line interface for batch processing
- TTA (Test-Time Augmentation) for improved results

## Requirements

This project requires Python 3.7+ and the following dependencies (specified in requirements.txt):
- PyTorch (install from https://pytorch.org/get-started/locally/)
- librosa
- matplotlib
- opencv-python
- resampy
- tqdm
- numpy

## Installation

1. Clone the repository
```
git clone https://github.com/phamngocson/Vocal_Remover.git
cd Vocal_Remover
```

2. Install dependencies
```
pip install -r requirements.txt
```

3. Install PyTorch according to your system (see https://pytorch.org/get-started/locally/)

## Usage

### Separating Vocals from a Track

```
python inference.py --input [music_file.mp3] --output_dir [output_directory]
```

This will generate two files:
- `[filename]_Instruments.wav`: The instrumental track
- `[filename]_Vocals.wav`: The isolated vocals

### Additional Options

- `--gpu`: Specify GPU device number (default: -1, CPU)
- `--tta`: Enable Test-Time Augmentation for better quality
- `--postprocess`: Apply post-processing to reduce artifacts
- `--output_image`: Generate spectrograms as images

### Training Your Own Model

1. Prepare a dataset with pairs of mixed audio and vocal-only tracks
2. Run the training script:
```
python train.py --dataset [dataset_directory] --batchsize 4 --epoch 200
```

## Credits

Developed and maintained by Phạm Lê Ngọc Sơn.

## License

This project is licensed under the terms included in the LICENSE file.
