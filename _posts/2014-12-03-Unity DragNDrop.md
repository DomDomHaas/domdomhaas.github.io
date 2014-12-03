---
layout: post
title: DragNDrop in the UnityEditor
---

<a href="http://docs.unity3d.com/ScriptReference/DragAndDrop.html" target="_blank">DragAndDrop for Unity</a> is not too understandable...  

{% highlight c# %}

    // Description in the Unity Docs

    DragAndDrop.GetGenericData
    static object GetGenericData(string type);
    Description

    Get data associated with current drag and drop operation.

{% endhighlight %}


When you're reading this, you proably think something like:

![confused]({{ site.baseurl }}/images/smileys/angry_small.png)


Not exctaly much information... In my case I wanted to be able to drag the color from a ColorPalette to on a GameObject in the Hierachy.
Turns out it's not possbile, at least not via Inspector Script, maybe it is possible to do with an own (Unity) EditorWindow.

Here's a basic snippet to test all the Events in the Editor to understand when and how they occour.
You have to start the click / drag in the inspector window.

{% highlight c# %}

    public void checkDragNDrop ()
    {

            switch (Event.current.type) {

            case EventType.MouseDown:
                // reset the DragAndDrop Data
                DragAndDrop.PrepareStartDrag ();

                Debug.Log ("MouseDown");

                break;

            case EventType.DragUpdated:

                DragAndDrop.visualMode = DragAndDropVisualMode.Copy;

                Debug.Log ("DragUpdated " + Event.current.mousePosition);
                break;

            case EventType.DragPerform:

                DragAndDrop.AcceptDrag ();
                Debug.Log ("Drag accepted");

                break;
                
            case EventType.MouseDrag:
                DragAndDrop.StartDrag ("Dragging");

                Debug.Log ("MouseDrag: " + Event.current.mousePosition);

                Event.current.Use ();
                break;
                
            case EventType.MouseUp:
                Debug.Log ("MouseUp had " + DragAndDrop.GetGenericData (dragColorKey));

                 // Clean up, in case MouseDrag never occurred:
                DragAndDrop.PrepareStartDrag ();

                break;

            case EventType.DragExited:

                Debug.Log ("DragExited");
                break;
            }

    }

{% endhighlight %}


***

What you will find is that "DragExited" comes as soon as you leave the inspector window. You can still use the basic events like EventType.MouseDown / MouseUp, but the one from UnityEditor (DragPerform + DragUpdate) will not occur anymore. Which means you can't use Unitys own Drag'n'Drop classes to drag something from the inspector window into the Hierachy or Sceneview.

I didn't want to write a drag'n'drop logic myself so I figured why not drag an GameObject from the Hierachry on to the Colorpalette? Which is apprently the way it's designed.

And it means the inspector window is on the receiving side, so only the DragUpdated and DragPerform has to be implemented.

The following snippet shows the drag'n'drop events in the inspector script ( <a href="https://gist.github.com/DomDomHaas/bad737591dcf51896eca" target="_blank">here is the full script</a> )
It can be easily check via contains() from the Rect class.

{% highlight c# %}

		private void checkDragable (Rect colRect, Color col)
		{

				string DragKey = "Color";

				if (Event.current.type == EventType.DragUpdated
						&& colRect.Contains (Event.current.mousePosition)) {
			
						// if ok show texture Color
						//if (gotDragableWithRender (DragAndDrop.objectReferences)) {
						DragAndDrop.visualMode = DragAndDropVisualMode.Copy;
				
						if (DragAndDrop.GetGenericData (DragKey) == null) {
								DragAndDrop.SetGenericData (DragKey, col);
						}
				
/*						} else {
								// show a rejected sign on the mousecursor
								DragAndDrop.visualMode = DragAndDropVisualMode.Rejected;
						}
*/			
						Event.current.Use ();
				}
		
				if (Event.current.type == EventType.DragPerform
						&& colRect.Contains (Event.current.mousePosition)) {
			
						Color color = (Color)DragAndDrop.GetGenericData (DragKey);
			
			
						//if (gotDragableWithRender (DragAndDrop.objectReferences)) {
						applyColorToRenderer (DragAndDrop.objectReferences, color);
						//}
			
						Event.current.Use ();
				}

		}
{% endhighlight %}



Did you like this post? Please consider a small donation:

<div class="flatter_button">
    <a href="https://flattr.com/submit/auto?user_id=DomDomHaas&url=http%3A%2F%2Fdomdomhaas.github.io%2FColorPaletteImporter%2F" target="_blank"><img src="//api.flattr.com/button/flattr-badge-large.png" alt="Flattr this" title="Flattr this" border="0"></a>
</div>

![please]({{ site.baseurl }}/images/smileys/please_small.png)