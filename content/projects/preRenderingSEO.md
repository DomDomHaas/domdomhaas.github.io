# SEO in SPA Web apps

Single page applications (SPA) have only one html which is changed via javascript (vue, react, svelte) during runtime.
With vue-meta and similar libraries it's possible to add meta tags to each page of a SPA-website.
But it still this means search engine bots would need to fully load the application to crawl all the information for each page.
As of around April 2025 this doesn't really seem to work.

## SSR vs Pre-rendering

Two common approaches are Server Side Rendering (SSR) or Pre-Rendering.
The goto framework for vue applications is nuxt, but to get from a regular
vue project to a nuxt project requires refactoring. Nuxt delivers a few things out-of-the-box,
but it requires a certain folder structure. This would mean we would need to change the whole
codebase at once to until the application would be to be served. So basically a migration. 

And additionally it needs to be a node server for the application to run on.
Which in our current infrastructure would require further changes.

So I had a look at pre-rendering, specifically and found vike.dev. It's a meta-framework
and allows for gradually implement some of the pages for static pre-rendering.
Also dynamically providing jsonLD information.
