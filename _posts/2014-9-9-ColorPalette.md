---
layout: post
title: ColorPalette for Unity
---

This is a plugin for **Unity** too use **Color Palettes**

![ohhh]({{ site.baseurl }}/images/smileys/narrow_small.png)

Get it for **Free** at: <http://github.com/DomDomHaas/ColorPalette>


## How to setup

If you want to use only the ColorPaletts make sure to use following scripts from the [repo](http://github.com/DomDomHaas/ColorPalette):

* PaletteData.cs
* Palette.cs
* At least the PaletteInspector.cs from the Editor folder (it has to be put into a "Editor" folder)
* All files of the folder **JSONPersistent** (it's actually another Tool for saving things to a txt-file)


***



## How to use the Palette

Add the Palette.cs on a gameobject and start creating your palette. 

![Palette UI preview]({{ site.baseurl }}/images/colorpalette/Preview.png)

Open the "Change Color" Tab and start changing the colors and it's percentages.

Change a colors via the ColorPicker on the left or change the HexDecimal Value either on the "Change Color" Tab or directly in the Plaette Tab.

If you click on "Add Color" a new color (black by default) will be added to the right. "Remove last Color" will remove the last one on the right.

Make sure to click on the **Save-Button** once you're finished!
(If your using multiple gameobjects with Palettes scripts, make sure they have different names!)

***


## ColorPaletteImporter

The [**ColorPaletteImporter**](http://domdomhaas.github.io/ColorPaletteImporter/) does extract the colors from the HTML Page from the given link from [pltts.me](https://www.pltts.me) or [colourlovers.com](https://www.colourlovers.com).


***


## How to integrate it

The storing of the (hex) values is done by the JSONPersistency plugin, so you actually get two plugins in one

![_uuuuu_]({{ site.baseurl }}/images/smileys/uuuuu_small.png)


More on how to use the JSONPersistency is soon to come.


Basically the storing of the colors is done with the `myData.colors` and `myData.percentages`: 

{% highlight csharp %}

/* Class definition for the color data of the palette variables */
/* which will be stored to disk */

    public class PaletteData
    {
        public PaletteData ()
        {
        }

        [SerializeField]
        public Color[] colors;

        [SerializeField]
        public float[] alphas;

        [SerializeField]
        public float[] percentages;

        [SerializeField]
        public float totalWidth;

    }


/* This Class is used by the Plaette.cs and the PaletteImporterData.cs extends it */
        
{% endhighlight %}


Which means all the palette data can accessed like so:

{% highlight c# %}

// this isn't the best way to find and you should do it in the Awake() function!
Plaette yourAwesomePalette = GameObject.Find("NameOfGameObject").GetComponent<Palette>();

for (int i = 0; i < yourAwesomePalette.myData.colors.Length; i++) {
    Color col = yourAwesomePalette.myData.colors [i];
    float percent = yourAwesomePalette.myData.percentages [i];


    // do awesome stuff with your color plaette

}

{% endhighlight %}


***



If you found this Tool useful consider a small donation:

<div class="flatter_button">
    <a href="https://flattr.com/submit/auto?user_id=DomDomHaas&url=http%3A%2F%2Fdomdomhaas.github.io%2FColorPalette%2F" target="_blank"><img src="//api.flattr.com/button/flattr-badge-large.png" alt="Flattr this" title="Flattr this" border="0"></a>
</div>

Please... ![please]({{ site.baseurl }}/images/smileys/please_small.png)

