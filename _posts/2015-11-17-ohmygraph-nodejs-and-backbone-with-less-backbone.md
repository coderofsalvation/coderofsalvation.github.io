---
layout: post
title: ohmygraph! Nodejs and backbone with less backbone
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/XrE-KVrLSaI" frameborder="0" allowfullscreen></iframe>

<div class="message">
  Hi! In this post I'm showing you ohmygraph! an ORM for rest.
  
</div>

> UPDATE: It seems nowadays Backbone *does* support exotic api layouts by _overriding the REST sync_-function

# Why?

Backbone / Restangular easily generate a restclient, but only if it matches a certain api layout.
However, I needed a rest client generator which kindof works with any api.
On top of that, I wanted to add resource linking for api's which don't support it.

# Links

* [ohmygraph! npm module](https://www.npmjs.com/package/ohmygraph)
* [jsonschema references npm module](https://www.npmjs.com/package/json-ref-lite)    
* [backbonejs](http://backbonejs.org)
* [restangular](http://github.com/mgonto/restangular)

