# 🎛️ Neural Equalizer

A deep learning-powered audio equalizer that intelligently adjusts frequency bands to enhance sound quality, match target signatures, or adapt to listening environments in real time.

---

## 🚀 Features

- **AI-Driven EQ Suggestions** — Automatically recommends EQ curves based on audio content type (music, speech, podcast, etc.)
- **Real-Time Processing** — Low-latency inference pipeline optimized for live audio streams
- **Target Curve Matching** — Match any reference frequency response using neural optimization
- **Genre-Aware Profiles** — Pretrained models for Rock, Classical, Jazz, Hip-Hop, and more
- **Custom Training** — Fine-tune on your own audio preferences and headphone/speaker profiles
- **Cross-Platform** — Works on Linux, macOS, and Windows

---

## 🧠 How It Works

The Neural Equalizer uses a trained neural network to analyze the spectral characteristics of an audio signal and predict optimal gain adjustments across configurable frequency bands. The model is trained on a dataset of expert-curated EQ settings paired with audio features extracted via Short-Time Fourier Transform (STFT) and Mel spectrograms.

```
Audio Input → Feature Extraction (STFT/Mel) → Neural Network → EQ Gain Predictions → Processed Output
```

---

## 📦 Installation

### Prerequisites

- Python 3.9+
- PyTorch 2.0+
- PortAudio (for real-time processing)

### Clone & Install

```bash
git clone https://github.com/yourusername/neural-equalizer.git
cd neural-equalizer
pip install -r requirements.txt
```

### Optional: GPU Support

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

---

## ⚙️ Usage

### Process an Audio File

```bash
python equalize.py --input audio/sample.wav --output audio/output.wav --profile "hifi"
```

### Real-Time Mode

```bash
python equalize.py --realtime --device 1
```

### List Available Audio Devices

```bash
python equalize.py --list-devices
```

### Match a Target Curve

```bash
python equalize.py --input sample.wav --target curves/harman_target.csv
```

---

## 🗂️ Project Structure

```
neural-equalizer/
├── data/                  # Training datasets and raw audio samples
├── models/                # Pretrained model checkpoints
├── src/
│   ├── model.py           # Neural network architecture
│   ├── features.py        # Audio feature extraction
│   ├── equalizer.py       # Core EQ processing logic
│   ├── trainer.py         # Training pipeline
│   └── utils.py           # Helper utilities
├── curves/                # Reference frequency response curves
├── notebooks/             # Jupyter notebooks for experimentation
├── tests/                 # Unit and integration tests
├── equalize.py            # Main entry point
├── train.py               # Training script
├── requirements.txt
└── README.md
```

---

## 🏋️ Training Your Own Model

```bash
python train.py \
  --data_dir data/training \
  --epochs 50 \
  --batch_size 32 \
  --lr 1e-4 \
  --output_dir models/custom
```

Training data should be organized as paired `(audio_file, eq_settings.json)` entries. See `data/README.md` for the expected format.

---

## 📊 Model Architecture

| Component        | Details                           |
|------------------|-----------------------------------|
| Input Features   | 128-band Mel Spectrogram          |
| Backbone         | CNN + Bidirectional LSTM          |
| Output           | Gain values for N EQ bands (dB)   |
| Loss Function    | MSE + Perceptual Spectral Loss    |
| Inference Speed  | ~4ms per frame (GPU) / ~18ms (CPU)|

---

## 🧪 Running Tests

```bash
pytest tests/ -v
```

---

## 🛣️ Roadmap

- [ ] VST3 / AU plugin wrapper for DAW integration
- [ ] Web UI for browser-based equalization
- [ ] Personalization via user listening feedback
- [ ] Headphone compensation profiles (AutoEQ integration)
- [ ] ONNX export for edge device deployment

---

## 🤝 Contributing

Contributions are welcome! Please open an issue first to discuss what you'd like to change.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add my feature'`)
4. Push and open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgements

- [LibROSA](https://librosa.org/) — Audio analysis library
- [PyTorch](https://pytorch.org/) — Deep learning framework
- [AutoEQ](https://github.com/jaakkopasanen/AutoEq) — Headphone measurement data
- [Harman Target Curve](https://www.harman.com/documents/AudioScienceReview.pdf) — Reference EQ target

---

> Built with ❤️ for audiophiles and engineers who believe sound can always be better.
