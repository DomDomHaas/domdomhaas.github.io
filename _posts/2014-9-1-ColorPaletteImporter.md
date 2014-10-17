---
layout: post
title: ColorPaletteImporter for Unity
---

This is a plugin for **Unity** too import **Color Palettes** directly from [pltts.me](https://www.pltts.me) or [colourlovers.com](https://www.colourlovers.com).
In addition to the functionality of the [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) the **ColorPaletteImporter** does extract the colors from the HTML Page from the given link.

Get it for **Free** at: <http://github.com/DomDomHaas/ColorPalette>


***


## How to setup


If you want to use the **ColorPalettImporter** make sure to include the all the scripts from [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) and also the follwing:

* PaletteImporterData.cs
* PaletteImporter.cs
* All files from the Editor folder
* **Additionally** add HtmlSharp (HtmlParser: https://github.com/wallerdev/htmlsharp extract at least the "HtmlSharp" folder into your asset folder)
* **Change the Playersettings** "API Compatibility Level" of Unity has to be set to ".NET 2.0" NOT ".NET 2.0 subset" (otherwise the System.Web is missing)

***



## How to use

Three steps of use it:

1. **Insert an url** which points directly to palette page of either a pltts.me or colourlovers.com
2. Click on **"Import palette from URL"** you should see a log message in the console what was downloaded and of course the palette in the editor window.
3. Make your changes to the Palette and don't forget to click on **"Save to File"** on ensure the colors and percentages will be stored and can be used next time your start up.

![_UI-preview_]({{ site.baseurl }}/images/colorpalette/Preview_Importer.png)


The **"load from file"** will be called in the Awake of the **ColorImporter** script.

***



## How to integrate it


Access the PlaetteImporterData like so:

{% highlight c# %}

// this isn't the best way to find and you should do it in the Awake() function!
PlaetteImporter yourAwesomePalette = GameObject.Find("NameOfGameObject").GetComponent<PaletteImporter>();

for (int i = 0; i < yourAwesomePalette.myData.colors.Length; i++) {
        Color col = yourAwesomePalette.myData.colors [i];
        float percent = yourAwesomePalette.myData.percentages [i];


        // do awesome stuff with your color plaette

}

{% endhighlight %}


See the **How to integrate it** part of the [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) more details!

***



Did you like this post? Please consider a small donation:

<div class="flatter_button">
    <a href="https://flattr.com/submit/auto?user_id=DomDomHaas&url=http%3A%2F%2Fdomdomhaas.github.io%2FColorPaletteImporter%2F" target="_blank"><img src="//api.flattr.com/button/flattr-badge-large.png" alt="Flattr this" title="Flattr this" border="0"></a>
</div>

![please]({{ site.baseurl }}/images/smileys/please_small.png)
