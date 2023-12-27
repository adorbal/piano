# 钢琴转录

本钢琴转录是将钢琴录音转录成 MIDI 文件的项目

## 配置环境
此代码库是使用 Python 3.7 和 PyTorch 1.4.0 开发的（应该适用于其他版本，但尚未经过全面测试）。

安装相关库:
```
pip install -r requirements.txt
```

## 使用预训练模型进行钢琴转录（参考字节跳动模型）
The easiest way is to transcribe a new piano recording is to install the piano_transcription_inference package: https://github.com/qiuqiangkong/piano_transcription_inference with pip as follows: 

```
pip install piano_transcription_inference
```

Then, execute the following commands to transcribe this [audio](resources/cut_liszt.mp3).

```
from piano_transcription_inference import PianoTranscription, sample_rate, load_audio

# Load audio
(audio, _) = load_audio('resources/cut_liszt.mp3', sr=sample_rate, mono=True)

# Transcriptor
transcriptor = PianoTranscription(device='cuda')    # 'cuda' | 'cpu'

# Transcribe and write out to MIDI file
transcribed_dict = transcriptor.transcribe(audio, 'cut_liszt.mid')
```
