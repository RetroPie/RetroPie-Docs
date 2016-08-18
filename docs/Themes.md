# Install Emulationstation Themes

Alternate themes can be easily installed with the RetroPie Theme Installer.

RetroPie Setup Script >> Setup >> EmulationStation Themes

Access the ui settings from the start menu in emulationstation

![emumenu](https://cloud.githubusercontent.com/assets/10035308/10356602/0b45279e-6d36-11e5-94be-2f6e56611f77.png)

change to your new theme (you may need to press f4 or quit to refresh emulationstation in order for the theme to load)

![emutheme](https://cloud.githubusercontent.com/assets/10035308/10356601/0b44d06e-6d36-11e5-89f6-e471ffafa54e.png)


## White Screen of Death

There is a fundamental bug with EmulationStation where unique background images are not loaded dynamically so if you have more than ~10 systems (on most themes that have a unique wallpaper per system) you will start to get a white screen of death and nothing will show up. 

There are a few things you can do to fix the white screen of death:

- increase your GPU/CPU split (see [here](https://github.com/RetroPie/RetroPie-Setup/wiki/Memory-Split))

- remove some systems

- switch your theme to any Carbon, Pixel, Eudora, Turtle-Pi, or Canela variant (as they have one static background and therefore don't crash when you have many systems)

If you can't access the theme changer in emulationstation because it's a white screen, you can [ssh](https://github.com/RetroPie/RetroPie-Setup/wiki/SSH) into the pi and change the theme name back to carbon in the backend in `/home/pi/.emulationstation/es_settings.cfg`

#THEME GALLERY

Access theme gallery in the esthemes menu

![theme gallery](https://cloud.githubusercontent.com/assets/17664918/14839524/2d768814-0bc7-11e6-9c22-b9ea2bb6b36e.png)

|Theme|Preview|
| :---:| :---:|
|**carbon**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357566/b98bb728-6d40-11e5-96a8-fca55ea635e0.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png" width="500"></sub>|  
|**carbon-centered**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357595/25e08296-6d41-11e5-9533-46af51206fe2.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357596/25ee3d46-6d41-11e5-9941-d000c2804ad8.png" width="500"></sub>|
|**carbon-nometa**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357566/b98bb728-6d40-11e5-96a8-fca55ea635e0.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357631/8f456ff8-6d41-11e5-8f83-7e3468471ce2.png" width="500"></sub>|
|**Simple**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357699/54911870-6d42-11e5-820b-b8ce4b7a9a9f.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357698/548295e8-6d42-11e5-8f80-b03cb089e3d4.png" width="500"></sub>|
|**simple-dark**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357699/54911870-6d42-11e5-820b-b8ce4b7a9a9f.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357745/ef967c16-6d42-11e5-81fd-239ab3a864b2.png" width="500"></sub>|
|**color-pi**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357774/47a89f38-6d43-11e5-8a5e-b8aa5622e8bd.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357775/47a96404-6d43-11e5-96cc-cab237cd3f90.png" width="500"></sub>|
|**simplified-static-canela**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357831/1c173d24-6d44-11e5-9692-a1e67553eb64.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357830/1c076a16-6d44-11e5-8a2b-07d59b2b542f.png" width="500"></sub>|
|**zoid**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357854/722c6a0e-6d44-11e5-94b1-0527cec9db09.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357698/548295e8-6d42-11e5-8f80-b03cb089e3d4.png" width="500"></sub>|
|**space**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357909/0db01cc8-6d45-11e5-9448-179611db1a9e.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357910/0db09036-6d45-11e5-84f1-1ef1e4c7c00b.png" width="500"></sub>|
|**simplebigart**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357941/5c687a68-6d45-11e5-8c16-7e3d77364645.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357940/5c589ed6-6d45-11e5-81fd-e8b1d33a9991.png" width="500"></sub>|
|**clean-look**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357973/b3e94d44-6d45-11e5-8556-e9e1922c9a86.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357972/b3d8f020-6d45-11e5-8852-a89cab9bcc49.png" width="500"></sub>|
|**turtle-pi**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10357502/022981c8-6d40-11e5-875b-e535576dc57b.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10357504/05f5ebc0-6d40-11e5-8ac4-31712e0a6193.png" width="500"></sub>|
|**nbba**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/10358023/3d62f160-6d46-11e5-9383-23da3aad1951.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/10358022/3d53dac2-6d46-11e5-9e53-849cfffbc7e2.png" width="500"></sub>|
|**Pixel**|<sub><img src="https://cloud.githubusercontent.com/assets/10035308/12162973/0191f402-b4c6-11e5-9a52-5acefa37d0d1.png" width="500"><img src="https://cloud.githubusercontent.com/assets/10035308/12163003/5413a25c-b4c6-11e5-9207-fcc2d5fe69d3.png" width="500"></sub>|
|**Material**|<sub><img src="https://cloud.githubusercontent.com/assets/9311410/15695879/85662fd4-2779-11e6-98a1-bcb49a3d1272.png" width="500"><img src="https://cloud.githubusercontent.com/assets/9311410/15695894/978f62c0-2779-11e6-8d3b-0cb6ab3184d1.png" width="500"></sub>|
|**MetaPixel**|<sub><img src="http://i.imgur.com/du9o2nK.png" width="500"><img src="http://i.imgur.com/Z1tEebt.png" width="500"></sub>|

## Creating Your Own EmulationStation Theme

For an in depth tutorial see this thread [HERE](Creating-Your-Own-EmulationStation-Theme)

For the official documentation on themes see [HERE](https://github.com/Aloshi/EmulationStation/blob/master/THEMES.md)

