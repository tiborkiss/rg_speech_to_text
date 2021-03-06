# Wave2Net2 Sound Recognition

This repository uses wave2net2 model from hugging face transformers to create an ASR system.

## Installation
Installation guide is in the root of this repository, in README.md
## Inferencing
### via recorded audio
- run  `python asr_inference_recording.py` with parameters:
    - `--recording` or `-rec` : path to audio recording
    - `--model` or `-m`: path to saved wavenetctc model if not passed it will be downloaded (default = "")
    - `--tokenizer` or `-t` : path to saved wavenettokenizer model if not passed then it will be downloaded (default = "")
    - `--blocksize` or `-bs` : size of each audio block to be passed to model (default = 16000)
    - `--overlap` or `-ov` : overlapping between each loaded block (default = 0)
    - `--output` or `-out` : path to output file to save transcriptions. (not required)
    - `--device` or `-d` : device to use for inferencing (choices=["cpu", "cuda"] and default = cpu ie.. inference will be done in CPU) 
- example
    - `python asr_inference_recording.py --recording input/rec.ogg -bs 16000 -out output/transcription.txt`
    - `python asr_inference_recording.py --recording input/rec.ogg -bs 16000 -ov 1600 -out output/transcription.txt`
    - `python asr_inference_recording.py --recording input/rec.ogg -bs 16000 -ov 1600 -out output/transcription.txt --device gpu`
    - `python asr_inference_recording.py --recording input/rec.ogg -bs 16000 -ov 1600 -out output/transcription.txt --device cpu`

### via live recording
- run  `python asr_inference_live.py` with parameters:
    - `--model` or `-m`: path to saved wavenetctc model if not passed it will be downloaded (default = "")
    - `--tokenizer` or `-t` : path to saved wavenettokenizer model if not passed then it will be downloaded (default = "")
    - `--blocksize` or `-bs` : size of each audio block to be passed to model (default = 16000)
    - `--output` or `-out` : path to output file to save transcriptions. (not required)
    - `--device` or `-d` : device to use for inferencing (choices=["cpu", "cuda"] and default = cpu ie.. inference will be done in CPU) 
- example
    - `python asr_inference_live.py -bs 16000 -out output/transcription.txt`
    - `python asr_inference_live.py`
    - `python asr_inference_live.py --device cuda`
    - `python asr_inference_live.py --device cpu`

### GPU inference vs CPU inference
For 4min 10sec recorder audio
    - GPU (Nvidia GeForce 940MX) : 18.29sec
    - CPU : 116.85sec

## To do list
- Environment Setup ✔
- Inferencing with CPU ✔
- Inferencing with GPU ✔
- Converting model to tensorflow with onnx for inference using tensorflow
- Training and Finetuning

## Tested Platforms
- native windows 10 ✔
- windows-10 wsl2 cpu
- windows-10 wsl2 gpu
- Ubuntu