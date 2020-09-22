---
layout: post
title:  "Ideas for the Future"
date:   2020-09-22 14:34:25
categories: technical
tags: technical
image: /assets/article_images/hebrew-manuscript-bg.jpg
---
Recently I was telling someone about what stuff I'm working on with <https://parabible.com> and I realised there's quite a bit.

So here's a brief summary:

# Frontend:

1. I have this idea to "appify" parabible a bit more: <https://jcuenod.github.io/parabible-experiments/docking-ui/dist/index.html> but that's a radical break from the UI approach I've taken thus far and I'm not sure it's a good one.
1. I am seriously considering abandoning react in favour of either inferno, vue, svelte, or vanilla js for performance reasons. React seems to choke a bit with millions of spans for all the clickable nodes (especially with search results). If I leave react, I might have to abandon my UI framework which raises separate questions.
1. I've got the search results window half rewritten with pagination in order to help mitigate the previous problem (but this raises backend questions as well).
1. I'm considering tearing search results out of the main window because (1) it might help with performance and (2) it might give me an opportunity to create some system of sharable searches which I think would be pretty awesome. I don't really have a good idea about how to make (2) happen though with just urls (other than storing searches on the server, which is not preferable because right now parabible is stateless) which is delaying this ever becoming reality...
1. Along the lines of abandoning react, I'm considering spectre.css (which may require a bunch of work to get it into a component framework). But I've looked at bulma and actually, I came up with my own design: <https://jcuenod.github.io/labs/app.html>
1. I have this NLP thing that I think could be awesome as a way of building a search but I don't think it's going to be > 70% reliable so it really needs to be the secondary way of doing searches (also the API for it is owned by facebook and they're forcing me to log in with facebook, which I can't do because I've never had an fb account and I refuse to get one). So I'll need to retrain the language model anyway but I'd love to do this with OpenAI's GPT-3 api if that were at all possible... This is honestly near the bottom of the list of priorities because the pace at which NLP is improving makes the cost of working on it when it takes a lot of work now very high.

# Backend:
1. Search results just get returned in a gigantic lump (and get truncated if there are too many [I think > 500]). I want to rather give a gigantic lump of nodes (or maybe a bunch of pages of nodes but I don't store the search and its results on the server and I don't know whether I want to rerun the search every time a new page is requested). Anyway, returning a bunch of nodes and having an API to return verses by node so the client can request individual verses is the direction I'm trying to go.
1. The current search loads all the data from a json file into memory which makes startup longer than necessary but is blazing fast for searching. The problem is the json is very obscure for outsiders to help optimizing. It should just be a db. But dbs were too slow. But now I want to search the LXX and the GNT and extending the json is a nightmare so I'm moving to a db which is actually made for this job. Search results will be slower but I've figured out some cool optimizations. (even so, graph dbs and olap dbs are not out of the question but I'm relatively far along with the postgres migration, as mentioned). I am pretty proud of the postgres solution I'm working on right now. It can do relatively horrifying queries that return tons of results in decent time (some queries are still too expensive, though - but not the reasonable ones, I don't think). You can see the start of this here: <https://github.com/jcuenod/pb2-data-server> (and the cool searches: <https://github.com/jcuenod/pb2-query-test>)
1. I'm not sure whether I actually want all this code in js. I'd kind of like to experiment with deno a bit but I'm considering Go because node doesn't have an actual postgres library that streams results as it retrieves them and I think using websockets might make things much snappier. This is something that is very backburner-ish
1. I think a well documented API would be mind-blowingly good to have but I don't have any experience with API design and so my approach is to just hack it together as necessary and break it if I want. This is also not good for anyone else who might consider using the platform for anything.
1. A critical move to an alternative db structure is that I want to be able to build the database using some kind of pipeline. This pipeline needs to be modular because a really good reason to start this process is that I want to pull in Chinese and Spanish translations (which raises UI issues for how to expose them). I also eventually want to get tagged version of the dead sea scrolls and the apostolic fathers into parabible (some of this data is already available! ). I've done a bit of work on the pipeline but (1) the design of the db is not set in stone and I keep having second thoughts about it, (2) solving the problem of putting texts in parallel is not trivial in my mind right now and I feel like I have mental race conditions to resolve before the pipeline will work without ugly hacks. This is probably my primary focus right now. You can see bits of that here: <https://github.com/jcuenod/parabible-data-pipeline>

