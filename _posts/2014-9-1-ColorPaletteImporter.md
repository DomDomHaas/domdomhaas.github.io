---
layout: post
title: ColorPaletteImporter for Unity
---

This is a plugin for **Unity** too use **Color Palettes** from [pltts.me](https://www.pltts.me) or [colourlovers.com](https://www.colourlovers.com).

Get it at: <http://github.com/DomDomHaas/ColorPalette>

In addition to the functionallity of the [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) the **ColorPaletteImporter** does extract the colors from the HTML Page from the given link.

***


## How to setup


If you want to use the **ColorPalettImporter** make sure to include the all the scripts from [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) and also the follwing:
- PaletteImporterData.cs
- PaletteImporter.cs
- All files from the Editor folder
- **Additionally** add HtmlSharp (HtmlParser: https://github.com/wallerdev/htmlsharp extract at least the "HtmlSharp" folder into your asset folder)
- **Change the Playersettings** "API Compatibility Level" of Unity has to be set to ".NET 2.0" NOT ".NET 2.0 subset" (otherwise the System.Web is missing)

***



## How to use

Three steps of use it:

1. **Insert an url** which points directly to palette page of either a pltts.me or colourlovers.com
2. Click on **"Import palette from URL"** you should see a log message in the console what was downloaded and of course the palette in the editor window.
3. Make your changes to the Palette and don't forget to click on **"Save to File"** on ensure the colors and percentages will be stored and can be used next time your start up.

![_UI-preview_]({{ site.baseurl }}/images/colorpalette/Preview_Importer.png)


The **"load from file"** will be called in the Awake of the **ColorImporter** script.
If your using multiple gameobjects with ColorImporter scripts, make sure they have different names!

***



## How to integrate it


Access the PlaetteImporterData like so:

{% highlight c# %}

    // this isn't the best way to find and you should do it in the Awake() function!
    PlaetteImporter yourAwesomePalette = GameObject.Find("TheNameOfYourGameObject").GetComponent<PaletteImporter>();

    for (int i = 0; i < yourAwesomePalette.myData.colors.Length; i++) {
            Color col = yourAwesomePalette.myData.colors [i];
            float percent = yourAwesomePalette.myData.percentages [i];
    
    
            // do awesome stuff with your color plaette
            
    }

{% endhighlight %}


See the **How to integrate it** part of the [**ColorPalette**](http://domdomhaas.github.io/ColorPalette/) more details!

***


And that's it so far, contributation is always welcome: <http://github.com/DomDomHaas/ColorPalette>

