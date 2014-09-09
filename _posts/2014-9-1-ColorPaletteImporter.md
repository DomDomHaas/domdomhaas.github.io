---
layout: post
title: ColorPaletteImporter for Unity
---

This is a plugin for **Unity** too use **Color Palettes** from [pltts.me](https://www.pltts.me) or [colourlovers.com](https://www.colourlovers.com).

Get it at: <http://github.com/DomDomHaas/ColorPalette>

The **ColorPaletteImporter** does extract the colors from the HTML Page from the given link, so in order to make that work a few steps are needed.

***


## How to setup

1. Download: [HTMLSharp](https://github.com/wallerdev/htmlsharp) an HTMLParser for C#
2. Extract the **"HTMLSharp" Folder** into your Asset folder of your Unity project
3. Set your Playersettings "API Compatibility Level" to **".NET 2.0"** not _".NET 2.0 subset"_ (otherwise the System.Web is missing)

***



## How to use

Three steps of use it:

1. **Insert an url** which points directly to palette page of either a pltts.me or colourlovers.com
2. Click on **"Import palette from URL"** you should see a log message in the console what was downloaded and of course the palette in the editor window.
3. If you have the correct Palette click on **"Save to File"** on ensure the colors and percentages will be stored and can be used next time your start up.

![_UI-preview_]({{ site.baseurl }}/images/colorimporter/UI_preview.png)


The **"load from file"** will be called in the Awake of the **ColorImporter** script.
If your using multiple gameobjects with ColorImporter scripts, make sure they have different names!

***



## How to integrate it

The storing of the (hex) values is done by the JSONPersistency plugin, so you actually get two plugins in one ![_uuuuu_]({{ site.baseurl }}/images/smileys/uuuuu_small.png)


More on how to use the JSONPersistency is soon to come.


Basically the Persistency is done with the `myData`: 

{% highlight csharp %}

    /* Class definition for the color data of the palette variables which will be stored to disk */

		public class PaletteData
		{
				public PaletteData ()
				{
				}

				[SerializeField]
				public Color[]
						colors;

				[SerializeField]
				public float[]
						alphas;

				[SerializeField]
				public float[]
						percentages;
				
				[SerializeField]
				public float
						totalWidth;

		}


/* This Class is used by the Plaette.cs and the PaletteImporterData.cs extends it */
        
{% endhighlight %}


Which means all the palette data can accessed like so:

{% highlight c# %}
    for (int i = 0; i < myImporter.myData.colors.Length; i++) {
            Color col = myImporter.myData.colors [i];
            float percent = myImporter.myData.percentages [i];
    
    
            // do awesome stuff with the color plaette
            
    }

{% endhighlight %}

***


And that's it so far, contributation is always welcome: <http://github.com/DomDomHaas/ColorPalette>


