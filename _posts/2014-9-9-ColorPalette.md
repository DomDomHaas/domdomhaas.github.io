---
layout: post
title: ColorPalette for Unity
---

This is a plugin for **Unity** too use **Color Palettes** get it at: <http://github.com/DomDomHaas/ColorPalette>

The [**ColorPaletteImporter**](http://domdomhaas.github.io/ColorPaletteImporter/) does extract the colors from the HTML Page from the given link from [pltts.me](https://www.pltts.me) or [colourlovers.com](https://www.colourlovers.com).

***


## How to setup

If you want to use only the ColorPaletts make sure to use following scripts from the [repo](http://github.com/DomDomHaas/ColorPalette):
- PaletteData.cs
- Palette.cs
- At least the PaletteInspector.cs from the Editor folder (it has to be put into a "Editor" folder)
- All files of the folder **JSONPersistent** (it's actually another Tool for saving things to a txt-file)


***



## How to use the Palette

Add the Palette.cs on a gameobject and start creating your palette.

![Palette UI preview]({{ site.baseurl }}/images/colorpalette/Preview.png)

Open the "Change Color" part and start changing the colors and it's percentages. Make sure to click on the **Save-Button** once you're finished!
(If your using multiple gameobjects with ColorImporter scripts, make sure they have different names!)

***



## How to integrate it

The storing of the (hex) values is done by the JSONPersistency plugin, so you actually get two plugins in one ![_uuuuu_]({{ site.baseurl }}/images/smileys/uuuuu_small.png)


More on how to use the JSONPersistency is soon to come.


Basically the storing of the colors is done with the `myData.colors` and `myData.percentages`: 

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

// this isn't the best way to find 
Plaette yourAwesomePalette = GameObject.Find("TheNameOfYourGameObject").GetComponent<Palette>();

    for (int i = 0; i < yourAwesomePalette.myData.colors.Length; i++) {
            Color col = yourAwesomePalette.myData.colors [i];
            float percent = yourAwesomePalette.myData.percentages [i];
    
    
            // do awesome stuff with your color plaette
            
    }

{% endhighlight %}

***


And that's it so far, contributation is always welcome: <http://github.com/DomDomHaas/ColorPalette>


