
### Creative Lead

EnviDat started as a prototype and the project itself was something like a R & D project within the WSL. EnviDat was something like a startup in a non-profit organization. The user acceptance wasn't a given thing, as the researchers had no obligation to choose EnviDat to publish their data over other alternatives like Zenodo or Invenio. 

Therefore it was clear: we had to proof the value of EnviDat for the researchers at the WSL. We did so not only on the basis of functionality but also of visual appeal and ease of use. My background in Game Design provided me a unique perspective on the topic of user interaction, visual feedback and communication.

![Data Library Metaphor](/images/projects/envidat/jaredd-craig-HH4WBGNyltc-unsplash.webp)
<small>Data Library Metaphor - Image by Jaredd Craig on Unsplash</small>


I've shaped the vision of EnviDat being the data library for environmental research data. We used this metaphor to communicate great the importance and the potential of EnviDat has for researchers, data scientist and the general public: Environmental research data needs to be openly available and we have to provide the services for the researcher for a smooth research data management experience.

<!-- ![Research Data Life Cycle](/images/projects/envidat/DataLifeCycle.webp)
<small>Research Data Life Cycle</small> -->


### Emotional Design


A major question for how to make the experience of data portal more connected to environmental science, for me that was quickly clear with environmental pictures.

![Dataset list](/images/projects/envidat/dataset_list_forest_small.webp)
<small>Screenshot of a list of <a href="https://envidat.ch/#/browse?tags=forest" target="_blank">datasets of the category forest</a></small>

WSL does research to three major categories: forest, snow and landscape.
Additionally to that sub categories of natural hazards, bio diversity and climate. This is reflected on the <a href="https://envidat.ch/" target="_blank">home page of EnviDat</a> by the keywords which can be used to filter the research datasets:

![research categories](/images/projects/envidat/research_categories.webp)

And influences the appearance of the dataset in the list.

![Dataset list](/images/projects/envidat/dataset_list_hazard_small.webp)
<small>Screenshot of a list of <a href="https://envidat.ch/#/browse?tags=hazard" target="_blank">datasets of the category hazard</a></small>


### UI Design

The design of EnviDat is based on the [material design from google (v2)](https://m2.material.io/) which is implemented by the [vuetify component library](https://vuetifyjs.com/en/introduction/why-vuetify/). This library provides behavior and styling, so according to the separation of [modular UI libraries of headless, boneless and skinless](https://nerdy.dev/headless-boneless-and-skinless-ui), it falls in the category of "fully loaded" / batteries included libraries (Additional good read about [headless and primitives](https://dev.to/danielkov/visual-primitives-and-headless-uis-a-modern-ui-library-trend-19jk)).

This choice made sense as I started as a single frontend engineer on a 60% workload and using vuetify provided a material design implementation in vue.js out-of-the-box. That let me focus on the redesign and replace what was given by the CKAN CMS, I created the website from scratch with the focus on simplicity and usability.


However using vuetify also came at a cost, as we had to delay the migration from vue version 2 to 3 due vuetify taking pretty long to release their version 3 (based on vue 3) and once it was released, multiple components weren't re-implemented yet. Most notably the component for date picking, which we used and we didn't want to build in a temporary solution only to replace it once again after a few months.


### Logo Design

The hexagonal shape of the logo represents an abstract data structure without being connected to specific WSL research topics. The shadows and corresponding light-effects make the eyes of an observer linger on the logo trying to understand its structure. This helps making the logo memorable.
In summary, the new EnviDat logo has a simple and unique look and feel of the two main **E**nvi**D**at letters integrated in a hexagonal shape.

![EnviDat Logo](/images/projects/envidat/Logo_overview_small.webp)
<small>Final Logo proposed to the directorate of WSL</small>





### Presentations & Poster Design

The challenge in communication scientific topics is often that it is based on a lot of information or every specific knowledge, breaking it down it in simple understandable terms is important. I created presentations and posters for various scientific events in the environmental research community, these were about scientific activities of the EnviDat team. 



![Poster: EnviDat Monitoring Data](/images/projects/envidat/EnviDat_Poster_Monitoring_data_small.webp)
<small>Poster: EnviDat Monitoring Data</small>



![Poster: Open Science Support By EnviDat](/images/projects/envidat/EnviDat_Poster_FOREMA_GIS_small.webp)
<small>Poster: Open Science Support By EnviDat</small>

