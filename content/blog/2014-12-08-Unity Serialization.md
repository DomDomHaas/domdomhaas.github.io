---
layout: post
title: Unity Serialization and persistency
---

Unity Serialization is pretty good for primitive datatypes, as far a I know, but if you use it for bigger things it as some fundamental flaws.
(ex. <a href="http://www.reddit.com/r/Unity3D/comments/2e9vlg/unity_serialization_is_truly_fubar/" target="_blank">http://www.reddit.com/r/Unity3D/comments/2e9vlg/unity_serialization_is_truly_fubar/</a>, <a href="http://blogs.unity3d.com/2014/06/24/serialization-in-unity/" target="_blank" >http://blogs.unity3d.com/2014/06/24/serialization-in-unity/</a>, etc.)

In my case I wanted to have a **connection of a component and a file** and it should be persistent. The InstanceID of an Component (aswell as from the GameObject) isn't any use because it is different every a scene loads.

![confused]({{ site.baseurl }}/images/smileys/shocked_small.png)


**Unity builtin** persistency connects GameObjects and it's component to the scene file via the **"m_LocalIdentfierInFile"** (you can see it if you change the inspector view to Debugmode).
I like the misspelling... I wonder if it will be fixed in Untiy 5? :)

So I figured there must be a way to use the same part for my case. A main problem is that the UnityEngine doesn't expose how it works and as far as I could material on the i-net on it, it's done on the c++ side of the engine.

---

**Long story short:**
After trying many things I came up with a simple workaround, which is creating a copy of the "m_LocalIdentfierInFile" while being in the UnityEditor and saving it as serialized property.

**Spoiler:** It won't work for GameObjects / Components which are created during runtime. 


And here is how you can do it too: ![confused]({{ site.baseurl }}/images/smileys/narrow_small.png)


{% highlight c# %}
// This is a copy of the "m_localIndentiferInFile"
// (don't forget to use [Serializable] on the class)
[SerializeField]
private int persistentID = -1;
{% endhighlight %}


With the following snippet you can access the "m_LocalIdentfierInFile". Make sure it is surrounded with the **"#if UNITY_EDITOR"** and don't use "using UnityEditor;" otherwise you can't create a build!

{% highlight c# %}
// Init this instance, it's public so it can be called from a InspectorScript
// is only set via the unity editor
public void init ()
{
    #if UNITY_EDITOR
    PropertyInfo inspectorModeInfo =
    typeof(UnityEditor.SerializedObject).GetProperty ("inspectorMode",
    BindingFlags.NonPublic | BindingFlags.Instance);

    UnityEditor.SerializedObject serializedObject = 
    new UnityEditor.SerializedObject (comp);

    inspectorModeInfo.SetValue (serializedObject, UnityEditor.InspectorMode.Debug, null);

    UnityEditor.SerializedProperty localIdProp =
    serializedObject.FindProperty ("m_LocalIdentfierInFile")  

    //Debug.Log ("found property: " + localIdProp.intValue);

    persistentID = localIdProp.intValue;
    //Important set the component to dirty so it won't be overriden from a prefab!
    UnityEditor.EditorUtility.SetDirty (this);
    #endif
}
{% endhighlight %}

(This snippet was provided by **"thelackey3326"** in <a href="http://forum.unity3d.com/threads/how-to-get-the-local-identifier-in-file-for-scene-objects.265686/" target="_blank">this UnityForum post</a>. )
With the addition of the **"UnityEditor.EditorUtility.SetDirty (this);"** line, **very important** to prevent prefabs from overriding the persistentID!

Here an InspectorScript snippet which uses OnEnable() to call the init() method.

{% highlight c# %}
public void OnEnable ()
{
    myPersist.init ();
}
{% endhighlight %}


This only works once the scene is saved (before there is no "m_LocalIdentfierInFile" meaning it is == 0) and it also means, you have create a gameobject (or drag'n'drop a prefabe), save the scene and click at least **ONCE** on the Gameobject!



Usually if you drag an Prefab into a scene you will at some point click on it and do something with it, but it's not a very nice workflow.

![confused]({{ site.baseurl }}/images/smileys/confused_small.png)

There is the possibility to hook in when the scene is **being saved**, unfortunately Unity doesn't provide a function to hook in **after** a scene was saved. So here's a code snippet to call the init() function before a scene is saved.

{% highlight c# %}
    static string[] OnWillSaveAssets (string[] paths)
    {
        Object[] objs = Component.FindObjectsOfType (typeof(PersistObject));
        //Debug.Log ("OnWillSaveAssets " + objs.Length);
        foreach (Object obj in objs) {
                PersistObject persist = (PersistObject)obj;
                persist.init ();
        }

        return paths;
    }
{% endhighlight %}

(Find the <a href="https://gist.github.com/DomDomHaas/74b337f8c061fa096185" target="_blank">full script on my Gist</a> it's specific for my implementation so copy/paste won't work directly, but you can see how it works. The main thing is that you inherit from "AssetModificationProcessor".)

Using that hook means: if you create an GameObject which uses the Editor-Snippet to get the "m_LocalIdentfierInFile" you have to save the scene at least twice after that. First time to set the "m_LocalIdentfierInFile" by Unity itself and second to store it in the local variable. It is not the most convenient way, but good enough, just setup a scene with the persistent GameObject first.



---


Was my nerd work useful to you?

![please]({{ site.baseurl }}/images/smileys/nerd_small.png)

Please consider a small donation so I can get some fuel aka. coffee to dig into further programming problems:

<!--div class="flatter_button">
    <a href="https://flattr.com/submit/auto?user_id=DomDomHaas&url=http%3A%2F%2Fdomdomhaas.github.io%2FUnity%2520Serialization%2F" target="_blank"><img src="//api.flattr.com/button/flattr-badge-large.png" alt="Flattr this" title="Flattr this" border="0"></a>
</div-->

<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
    <input type="hidden" name="cmd" value="_s-xclick">
    <input type="hidden" name="hosted_button_id" value="Y6ZR43SA62TUG">
    <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif" border="0" name="submit" alt="PayPal - The safer, easier way to pay online!">
    <img alt="" border="0" src="https://www.paypalobjects.com/en_US/i/scr/pixel.gif" width="1" height="1">
</form>

<br/>

<script id='fbqki18'>(function(i){var f,s=document.getElementById(i);f=document.createElement('iframe');f.src='//api.flattr.com/button/view/?uid=DomDomHaas&url=http%3A%2F%2Fdomdomhaas.github.io%2FUnity%2520Serialization%2F';f.title='Flattr';f.height=62;f.width=55;f.style.borderWidth=0;s.parentNode.insertBefore(f,s);})('fbqki18');</script>

---

