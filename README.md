# project-wheatley
Making an animatronic Wheatley from Portal 2

## Goal
Wheatley is cool and we want to make a real-life version of him, as much as can be done with a video game character.

## Streams of work

### Voice
As all people should be aware, the voice of Wheatley belongs to the incomporable [Stephen Merchant](https://www.stephenmerchant.com/). His brilliant performance is part of what makes Wheatley a legend. Follow his career, you'll be glad you did.

As much as I would enjoy calling up Stephen and suggesting he live inside a 13" plastic ball in my house, offering him ridiculous sums of money for the privilege, I think in order to bring his voice to our replica we'll need to take...alternative steps.

There are a number of tools at our disposal that can replicate the speaking voice of another person, and since this is just a homespun product that I don't plan on selling or anything, I feel it's appropriate to utilize voice generation models.

Enter [coqui-ai TTS](https://github.com/coqui-ai/TTS). This will allow us to use Stephen's pre-recorded performance of Weatley's dialogue as an input to train a fit for purpose text-to-speech model that will, well, hopefully sound a bit like Mr. Merchant.

In order to obtain the audio for Wheatley's lines, we'll need a few things:
- [x] A copy of [Portal 2](https://store.steampowered.com/app/620/Portal_2/) (honestly, you need this anyway so just go buy it)
- [x] A tool to extract the game's VPK archives, I used the very excellent [Source 2 Viewer](https://valveresourceformat.github.io/)
- [ ] ~~A base plate of prefamulated amulite~~
- [ ] ~~Twelve medium geosynthetic membranes~~
- [ ] ~~Fish-shaped volatile organic compounds and sediment-shaped sediment~~

Turns out you just need the first two.

![image](https://github.com/mhitchens/project-wheatley/assets/1898713/f0f8886a-0267-45a7-bbc2-8f0425ff0653)

Wheatley's dialogue can be found in `sound/vo/wheatley`.

Installing TTS on Windows wasn't too difficult. Prerequisites to install:
- Python
- Git

Clone the repository to a folder of your choosing with `git clone https://github.com/coqui-ai/TTS.git`. Open a command window in the TTS folder. From there, create a Python virtual environment (a folder to contain your runtime, libraries, dependencies, scripts) with `python -m venv .\venv`. Then activate your virtual environment with `.\venv\Scripts\activate.bat`. Get your dependencies installed with `pip install -e .`.

Once you've gotten this far, you should have a working install of TTS. It comes with a commmand line tool for generating speech and storing it in WAV files. We tested an initial generation with one of Wheatley's lines where he's providing guidance on not smashing things.

`tts --text "Hello! Hi! Yes, welcome to Aperture Science! Yeah, it's brilliant here isn't it? Expensive, all this, you know." --model_name tts_models/multilingual/multi-dataset/xtts_v2 --language_idx en --speaker_wav "h:\Modding\Portal 2 VPK unpack\out\sound\vo\wheatley\bw_screen_smash21.wav"`

Okay, lots going on here, let's unpack.

`--text` is going to be the speech to synthesize. TTS will separate this into sentences.

`--model_name` TTS is not doing the heavy lifting of actually generating the speech, it's more of a framework and API around models that do. [XTTS2](https://huggingface.co/coqui/XTTS-v2) is an incredibly capable generation model that can handle multiple languages, and can model generated speech from sample audio, which is basically witchcraft if you, like me, grew up watching this technology explode over the years.

`--language_idx` is set to en for English, as this is a multilingual model AND WHEATLEY SPEAKS ENGLISH OKAY I KNOW SOME OF THESE ARE OBVIOUS.

`--speaker-wav` is an existing WAV file of someone speaking, which will be used to model the generated speech after. We started with just this one line, but you can also provide several.

And that will churn for a bit and chew up some CPU until, when finished, you'll be given a lovely `tts_output.wav` file to play.

```
(venv) H:\Code\github\coqui-ai\TTS>tts --text "Hello! Hi! Yes, welcome to Aperture Science! Yeah, it's brilliant here isn't it? Expensive, all this, you know." --model_name tts_models/multilingual/multi-dataset/xtts_v2 --language_idx en --speaker_wav "h:\Modding\Portal 2 VPK unpack\out\sound\vo\wheatley\bw_screen_smash21.wav"
 > tts_models/multilingual/multi-dataset/xtts_v2 is already downloaded.
 > Using model: xtts
 > Text: Hello! Hi! Yes, welcome to Aperture Science! Yeah, it's brilliant here isn't it? Expensive, all this, you know.
 > Text splitted to sentences.
['Hello!', 'Hi!', 'Yes, welcome to Aperture Science!', "Yeah, it's brilliant here isn't it?", 'Expensive, all this, you know.']
 > Processing time: 23.59095287322998
 > Real-time factor: 1.845030470939224
 > Saving output to tts_output.wav
```

Our result was interesting, not overwhelmingly impressive, but as a first step, it's got the makings of something that can eventually be great.
