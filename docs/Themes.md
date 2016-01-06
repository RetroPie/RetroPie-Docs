# Install Emulationstation Themes

Alternate themes can be easily installed starting with RetroPie 3.1 with the RetroPie Theme Installer.

Open Option 3 from the setup script

![setup script](https://cloud.githubusercontent.com/assets/10035308/10356537/6b708a24-6d35-11e5-8b86-edb1145b4af8.png)

Navigate to the theme installer

![theme installer](https://cloud.githubusercontent.com/assets/10035308/10356540/73510bd8-6d35-11e5-8a42-48b8d2239a37.png)

Install the themes you want

![themes](https://cloud.githubusercontent.com/assets/10035308/10356544/76b98700-6d35-11e5-8ab8-5e77aeca0ca4.png)

Access the ui settings from the start menu in emulationstation

![emumenu](https://cloud.githubusercontent.com/assets/10035308/10356602/0b45279e-6d36-11e5-94be-2f6e56611f77.png)

change to your new theme (you may need to press f4 or quit to refresh emulationstation in order for the theme to load)

![emutheme](https://cloud.githubusercontent.com/assets/10035308/10356601/0b44d06e-6d36-11e5-89f6-e471ffafa54e.png)


## White Screen of Death

There is a fundamental bug with EmulationStation where unique background images are not loaded dynamically so if you have more than ~10 systems you will start to get a white screen of death and nothing will show up. 

There are a few things you can do to fix the white screen of death:

- increase your GPU/CPU split (see [here](https://github.com/RetroPie/RetroPie-Setup/wiki/Memory-Split))

- remove some systems

- switch your theme to any Carbon, Eudora, or Canela variant (as they have one static background and therefore don't crash when you have many systems)

If you can't access the theme changer in emulationstation because it's a white screen, you can [ssh](https://github.com/RetroPie/RetroPie-Setup/wiki/SSH) into the pi and change the theme name back to carbon in the backend in `/home/pi/.emulationstation/es_settings.cfg`

#THEME GALLERY

<table style="width:100%">
<tr>
  <th>carbon</td>
  <th>carbon-centered</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357566/b98bb728-6d40-11e5-96a8-fca55ea635e0.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357595/25e08296-6d41-11e5-9533-46af51206fe2.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357596/25ee3d46-6d41-11e5-9941-d000c2804ad8.png" width="250"></td> 
</table>

<table style="width:100%">
<tr>
  <th>carbon-nometa</td>
  <th>simple</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357566/b98bb728-6d40-11e5-96a8-fca55ea635e0.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357631/8f456ff8-6d41-11e5-8f83-7e3468471ce2.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357699/54911870-6d42-11e5-820b-b8ce4b7a9a9f.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357698/548295e8-6d42-11e5-8f80-b03cb089e3d4.png" width="250"></td> 
</table>

<table style="width:100%">
<tr>
  <th>simple-dark</td>
  <th>color-pi</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357699/54911870-6d42-11e5-820b-b8ce4b7a9a9f.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357745/ef967c16-6d42-11e5-81fd-239ab3a864b2.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357774/47a89f38-6d43-11e5-8a5e-b8aa5622e8bd.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357775/47a96404-6d43-11e5-96cc-cab237cd3f90.png" width="250"></td> 
</table>

<table style="width:100%">
<tr>
  <th>simplified-static-canela</td>
  <th>zoid</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357831/1c173d24-6d44-11e5-9692-a1e67553eb64.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357830/1c076a16-6d44-11e5-8a2b-07d59b2b542f.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357854/722c6a0e-6d44-11e5-94b1-0527cec9db09.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357698/548295e8-6d42-11e5-8f80-b03cb089e3d4.png" width="250"></td> 
</table>

<table style="width:100%">
<tr>
  <th>space</td>
  <th>simplebigart</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357909/0db01cc8-6d45-11e5-9448-179611db1a9e.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357910/0db09036-6d45-11e5-84f1-1ef1e4c7c00b.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357941/5c687a68-6d45-11e5-8c16-7e3d77364645.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357940/5c589ed6-6d45-11e5-81fd-e8b1d33a9991.png" width="250"></td> 
</table>

<table style="width:100%">
<tr>
  <th>clean-look</td>
  <th>turtle-pi</td>
</tr>
<tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357973/b3e94d44-6d45-11e5-8556-e9e1922c9a86.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357972/b3d8f020-6d45-11e5-8852-a89cab9bcc49.png" width="250"></td> 
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10357502/022981c8-6d40-11e5-875b-e535576dc57b.png" width="250"><img src="https://cloud.githubusercontent.com/assets/10035308/10357504/05f5ebc0-6d40-11e5-8ac4-31712e0a6193.png" width="250"></td> 
  </tr>
</table>

<table style="width:100%">
<tr>
  <th>nbba</td>

</tr>
<td>
<img src="https://cloud.githubusercontent.com/assets/10035308/10358023/3d62f160-6d46-11e5-9383-23da3aad1951.png" width="250"></td> 
<tr>
</tr>
  <td><img src="https://cloud.githubusercontent.com/assets/10035308/10358022/3d53dac2-6d46-11e5-9e53-849cfffbc7e2.png" width="250"></td> 



<tr>

  </tr>
</table>