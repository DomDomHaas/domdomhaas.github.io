### Building EnviDat

In 2018 I started taking ownership of the new frontend of EnviDat. With the mission build a modern data portal for environmental sciences at WSL. Our focus point were: visual appeal, readability and good user experience.

Over the years we built an excellent platform which distinguishes itself from other research data portals. And along with it an effective team of research software engineers which provides scientific IT services for research units and projects at WSL.


![EnviDat Homepage](/images/projects/envidat/envidat_homepage_2.webp)
<small><a href="https://envidat.ch/" target="_blank">EnviDat Homepage</a></small>

The initial go-live release changed the appearance of all the publicly available pages. 

![EnviDat Dataset Listpage](/images/projects/envidat/envidat_browsepage.webp)
<small><a href="https://envidat.ch/#/browse/" target="_blank">EnviDat Dataset Listpage</a></small>


![EnviDat Dataset Detailpage](/images/projects/envidat/envidat_datasetpage.webp)
<small><a href="https://envidat.ch/#/metadata/experimental-rockfall-dataset-tschamut-grisons-switzerland" target="_blank">Dataset of an experimental campaign of induced rockfall in Tschamut</a></small>


Followed by incrementally replacing the pages for login and dashboard. Then the next major release redesigned the existing process of creating, editing and publishing dataset and implement additional functionalities.

Once users have signed in they see their dashboard:

![User Dashboard](/images/projects/envidat/envidat_dashboard.webp)
<small><a href="https://envidat.ch/#/dashboard" target="_blank">User Dashboard</a></small>

They can select a dataset to get into the workflow of editing a dataset:

![Dataset Workflow Edit mode](/images/projects/envidat/envidat_editing.webp)
<small>Dataset Workflow Edit mode <a href="https://envidat.ch/storybook/?path=/story/6-workflows-editing-workflow--editing-steps" target="_blank">Dataset Workflow Edit mode in Storybook</a></small>




### Software Architecture

The system architecture of EnviDat is a CSR aka. SPA build written in Vue with Typescript, Vuetify, Vite, Vitest, Storybook served from a S3 Bucket.
With the CKAN, a pyhton CMS in the backend, served with docker and multiple microservices (Solr, Redis) and nginx for the routing. The backend connects to a postgres DB server and any uploaded research data is stored in S3 Object buckets which can deal with large file storage >100GB.

A public proxy which serves the frontend and routes the api call to the backend and the S3 Buckets.


#### Frontend Architecture

Decoupling of the "business logic" and the UI rendering is ensured through a component-driven design with dependency injection. This has a few benefits:

- testability is increased
- code-splitting improved (fast loading of the website)
- and isolated development of the UI components


With [Storybook](https://storybook.js.org/) the components can be implemented easily with their different use-cases, it's a approach of a "visual" test driven design, similar to writing unit tests.

When integrated together to the website, each site has a main component the page, which decides on any events which the child components bubble up. It provides an dependencies via injection to the children components.


Here the dataset list in storybook:

![Dataset List in Storybook](/images/projects/envidat/storybook_metadatalist.webp)
<small><a href="https://envidat.ch/storybook/?path=/story/3-datasets-metadata-list--top-filtering-layout" target="_blank">Dataset List in Storybook</a></small>


### Senior Software Fullstack Engineer at WSL

I was responsible for the full software life cycle of the frontend EnviDat, taking care of the design, planning, testing and deployment of features. Over the years we grew from two to five software engineers and a product owner.

My responsibilities grew with the team. I introduced new team members to the frontend code base, made code reviews in the backend, Designed various Gitlab CI/CD pipelines.
I've supported team members with and programming concepts, gave support and guidance in all concerns of software engineering.

### Leadership

As Senior Software Engineer and later Lead Engineer I've supported engineers with feature planning, introduction best practices and software architectures, highlight testing and debugging strategies and providing feedback through code reviews.
I'd like a team culture of openness, cooperation so everyone can be authentic and inspiration each other to tackle technical and design challenges.



### DevOps

In 2022 we introduced DevOps and CI/CD pipelines via gitlab and started to "dockerize" the backend application and its microservices. Over time we fleshed out the pipelines for different environments, introducing remote docker deployment, automated tests, security checks, building of storybook and pre-rendered static html for SEO listing.

![Gitlab pipelines](/images/projects/envidat/envidat_devops.webp)
<small>Gitlab pipelines of the EnviDat Frontend</small>

Together with the product owner / project lead we planned and build the  infrastructure with apache / nginx proxies, vue frontend, phyton backend and S3 buckets for large file storage > 1 TB.




### Future of EnviDat

EnviDat the data portal established itself in the WSL and achieved a reach beyond the WSL and Switzerland. The team has provided research software engineering services to research projects in the WSL and with it showed its value to the research units.

In 2025 it was decided that EnviDat would transition from a project to a group within the organization of WSL, thus reflecting a long term commitment for scientific IT services and research software engineering.

