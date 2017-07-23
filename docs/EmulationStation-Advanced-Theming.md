## About This Tutorial

In this tutorial I'm going to take you through some of the more advanced features available when creating a theme for Emulationstation and RetroPie.

## Default Theme

Themes can now provide a default theme that will be used when then the theme does not provide specific support for a given system.  The default theme must be defined in `theme.xml` which is in the root of the theme directory.

An existing feature of EmulationStation is that the system logo will default to text if an image is not specified.  Additional theme options have been added for the logo text to give theme creators more control over the appearance.

Below is an example implementation of a default theme for [carbon](https://github.com/RetroPie/es-theme-carbon).  It is very similar to the existing system themes.  The main change is the addition of the `logoText` element.  In addition the paths for the logos have been adjusted to take advantage of the new theme variables feature.  In this case, it will try to load the logo image, if it is not found, then it will render the logo as text. 
```
<theme>
    <formatVersion>3</formatVersion>
    <include>./carbon.xml</include>

	<view name="system">

		<image name="ControllerOverlay" extra="true">
			<tile>false</tile>
			<pos>0.5 0.2</pos>
			<origin>0.5 0.5</origin>
			<size>0.3 0</size>
			<path>./art/controller/${system.theme}.svg</path>
			<!--<color>8b0000</color>-->
		</image>

		<image name="logo">
			<path>./art/logo/${system.theme}.svg</path>
		</image>

		<text name="logoText">
			<fontPath>./art/Cabin-Bold.ttf</fontPath>
			<color>${themeColor}</color>
			<forceUppercase>true</forceUppercase>
		</text>		
	</view>

	<view name="basic, detailed, video">

		<text name="logoText">
			<pos>0.0 0.02</pos>
			<size>0.460 0.126</size>
			<fontSize>0.12</fontSize>
			<fontPath>./art/Cabin-Bold.ttf</fontPath>
			<color>${themeColor}</color>
			<forceUppercase>true</forceUppercase>
		</text>
		<image name="logo">
			<path>./art/logo/${system.theme}.svg</path>
			<pos>0.266 0.074</pos>
			<maxSize>0.460 0.126</maxSize>
			<origin>0.5 0.5</origin>
		</image>
		
		<image name="logo2" extra="true">
			<path>./art/controller/${system.theme}.svg</path>
			<pos>0.874 0.074</pos>
			<maxSize>0.460 0.126</maxSize>
			<origin>0.5 0.5</origin>
			<color>bbbbbb</color>
		</image>
	</view>
</theme>
```

## Theme Variables

Coming Soon.

---

## System Carousel

Coming Soon.

---

## Adding Video Support

Coming Soon.

---