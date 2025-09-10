23.08.2022
# New Way of Editing Datasets

The main mission of the EnviDat team is to provide tools and services for WSL scientists.
Among other things, we are building the EnviDat website for publishing environmental research data since 2018. We started building a modern
website for all the publicly accessible parts of the platform and transitioned into the parts which are specific to each user.

Until now, scientists had to log in to the legacy website, what we sometimes refer to as CKAN website, to be able to manage their dataset and publish research data. 
Now users can directly log in into the EnviDat website and edit their datasets. Not all the functionality
of the legacy website is already migrated, but with the editing workflow we built out the foundation to migrate all the functionality
for managing research dataset in a modern way.

With that said, we would like to explain the new editing in this post.


### Prerequisite

For editing a dataset, you need these things: 
- EnviDat account (sign up via email on the homepage)
- Editor rights (ask the research data manager or leader of your group, they can write to envidat@wsl.ch to request access for you)
- At least one dataset created by yourself or a dataset where you're listed as collaborator
  
  
<br>
<br>


## New Editing Workflow

We introduced a dashboard which lists your datasets, your collaborations, and the datasets of the groups are in.
If you have editor rights (ask your group research data manager / group leader), you can start editing by clicking on the yellow pen icon.

You'll get to the first main step "Metadata" with the editing of the header information:

![Editing Research Header](https://s3-zh.os.switch.ch/frontend-static/blog/images/edit_workflow_title.gif "Editing Research Header")

Here is shown how the Research Data Title can be changed and how the contact person can
be picked from a list of existing authors. It's also possible to enter an email address and given-name and last name.


#### Previews

Once you are done editing your changes will be saved immediately, you will see a small preview of your metadata,
how it looks when other users are looking at your dataset. In the top right is an eye-icon which will
get you to the full view of your dataset, so you can see what it looks like when your dataset is published.

You can preview your unpublished dataset, but only users which have editing rights will be able to see a preview
of unpublished dataset.


### Description Of Your Research Data

The Description is a simple text-area, you can use markdown to make the
text better readable: [https://www.markdownguide.org/cheat-sheet](https://www.markdownguide.org/cheat-sheet)

When writing the description, keep interoperability in mind and try to write it so a scientist from an unrelated
field could understand what the data is about. Can you even describe it that a laypersons would understand it?

Once done, ask a colleague to review the description and give feedback.

### Research Data Keywords

While there are different recommendations for using keywords for papers (Read more: [https://blog.wordvice.com/choosing-research-paper-keywords/](https://blog.wordvice.com/choosing-research-paper-keywords/)
and [https://falconediting.com/en/blog/6-tips-for-choosing-keywords-for-your-scientific-manuscript  ](https://falconediting.com/en/blog/6-tips-for-choosing-keywords-for-your-scientific-manuscript) )  


The keywords in EnviDat are used when doing a full-text search, but also when filtering for
keywords directly. We limited the length of a keyword term to two words.
We think keywords that are longer than two words are too specific to be useful when searching for datasets. And that won't be useful when filtering a list of research datasets because they might only be used in one dataset.

EnviDat uses some basic keywords as broad research categories:

![Research Categories](https://s3-zh.os.switch.ch/frontend-static/blog/images/research_categories.jpg "Research Categories")

So we recommend using one of these broad keywords to get the dataset into a category (if it makes sense) and then use
more and more specific keywords to narrow down your keyword description.

When choosing keywords, you can pick them out from a list of existing ones. As show in the gif below.
If you don't find your keyword just type it and hit `enter`. 
Once saved, you'll see the preview next to it.

![Editing Keywords](https://s3-zh.os.switch.ch/frontend-static/blog/images/edit_workflow_keywords.gif "Editing Keywords Information")

What do you think about that usage of keywords on EnviDat? Let us know [via email](mailto:envidat@wsl.ch)

### Geospatial Information


Here is an example of applying an additional polygon to the geospatial information.

![Editing Geospatial Information](https://s3-zh.os.switch.ch/frontend-static/blog/images/edit_workflow_geoinfo.gif "Editing Geospatial Information")

It is possible to use a single point, multiple points, polygons and a combination of theses as
geospatial information.

If your dataset is showing a rectangle encompassing Switzerland, please consider updating the location
to more accurately to reflect where your data is coming from.



## Managing Data & Resources

The editing of data and resources is under construction for the new workflow, 
and for now the legacy website should be used. A resource can be selected
and a click on the edit icon will open directly into the editing view of this resource.


## Related Publications & Datasets

These two entries work in the same way as the description, please use correct citations for
paper publications. Please provide links to related datasets as a DOI if they are available.


## Publication Information

The publication of a dataset needs approval, normally there is a DOI
generated (this process occurs in the background and is not visible to users.)
This process isn't reflected in the editing workflow, click on the "Publish Dataset" button.
It will bring you to the legacy website showing your dataset. In the top right is the button
for publishing, please click it to start the publishing process.


### Editing Already Published Datasets

After publication, certain changes to a dataset are not allowed anymore.
You will see a small hint under an editing element showing like this: 

![Changes Not Allowed](https://s3-zh.os.switch.ch/frontend-static/blog/images/author_change_not_allowed.jpg "Research Categories")


## Enjoy Editing


We hope we can provide a more user-friendly and more focused experience for scientists when editing their datasets.
Thanks for reading and get in contact with the EnviDat team [via email](mailto:envidat@wsl.ch)



Credits:
- Blog header photo by [Kelly Sikkema](https://unsplash.com/@kellysikkema)
- Other images and text: EnviDat team
