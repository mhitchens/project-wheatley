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
