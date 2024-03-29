# Netplay

Some RetroArch cores have netplay built-in which means that if you have some friends in a different place and still want to play games with them you can.

There are a few stipulations that have to be met before you are able to utilise netplay:

- You both need to be running the same version of RetroArch
- You both need to be running the same emulator
- You both need to have the same exact ROM

## Configuration

So first things first- you need to set up your configurations for netplay:

you can access the netplay configurations from the RetroPie menu in EmulationStation or from the setup script.

One person needs to be the host, everyone else who tries to connect to the host will be clients

### Host

If you will be acting as the host...

- Set your Netplay Mode to host
- Change Host IP Address to your IP address
- Either go to your router settings and open the port 55435 for both TCP and UDP **or** change the TCP/UDP Port setting in RetroArch to one that's already open
- Select a number for Delay Frames. If you are experiencing a very low fps, try increasing this number.
- Pick a Nickname
- When launching a ROM to use netplay you'll open up the [runcommand menu](Runcommand#runcommand-launch-menu) by pressing `A` (or any key/button on your keyboard/gamepad) as your ROM loads and then you'll select launch netplay.

![host](https://cloud.githubusercontent.com/assets/10035308/10062467/1c89bb58-6220-11e5-942b-7892d4b82050.png)

Make sure to tell your friend:

- Your IP Address
- Your Open Port
- Your Delay Frames Number
- Your selected Core and ROM

### Client

If you will be joining a game...

- Set your Netplay Mode to Client
- Set Spectator Mode Enable to OFF
- Change Host IP Address to the IP Address your friend gave you
- Change TCP/UDP Port to the number your friend gave you
- Change Delay Frames to the number your friend gave you
- Pick a Nickname
- When launching a ROM to use netplay you'll open up the [runcommand launch menu](Runcommand) by pressing a button (or any key on your keyboard) as your ROM loads and then you'll select launch netplay

![client](https://cloud.githubusercontent.com/assets/10035308/10062468/2046ec02-6220-11e5-9d42-f58779986f93.png)

Now if you and your friend successfully followed all of these steps, your game should load. If it didn't, try checking if you have the same ROM, the same core and if your host's port is really open. If everything fails, consider switching server and client roles. 

## Windows

If you are on a Windows PC you can set up the network settings from the RGUI:

![settings](https://cloud.githubusercontent.com/assets/10035308/10062550/d0d17d8a-6220-11e5-8325-461c0d712668.png)
![network](https://cloud.githubusercontent.com/assets/10035308/10062551/d0d3dd5a-6220-11e5-910f-824cc081b902.png)

Note that the following are settings when running as a client:

![network3](https://cloud.githubusercontent.com/assets/10035308/10065131/9a09ef6c-623e-11e5-8b96-19c0254feb1a.png)

If you want the PC to be the host change Netplay Client Enable to off.
