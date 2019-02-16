[![Tweet about codecrumbs](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=Leave%20breadcrumbs%20in%20source%20code%20with%20codecrumbs%20tool%20&url=https://github.com/Bogdan-Lyashenko/codecrumbs&via=bliashenko&hashtags=javascript,code) [![npm version](https://badge.fury.io/js/codecrumbs.svg)](https://badge.fury.io/js/codecrumbs)

<p align="center">
    <img src="/docs/logo.png" width="200"/>
</p>

<h3 align="center">
  <a href="#what">What</a>
  <span> · </span>
  <a href="#demo">Demo</a>
  <span> · </span>
  <a href="#get-started">Get started</a>
  <span> · </span>
  <a href="#features">Features</a>
  <span> · </span>
  <a href="#case-studies">Case studies</a>
  <span> · </span>
  <a href="#support">Support</a>
  <span> · </span>
  <a href="#contribute">Contribute</a>
</h3>

## What
> **Have you ever got lost in a big or unknown codebase?** This tool will help you to solve that. Also, it will increase your development speed and give more knowledge about your application architecture. 
>
>**How it works?** You run `codecrumbs` command for a codebase, it analyzes source code and build its visual representation. Write down a codecrumb-comment and codebase state will be reflected by visual client in browser on the fly. 
>
>-[@bliashenko](https://twitter.com/bliashenko)    

## Demo
Check out the example of [**standalone version running here**](https://codecrumbs.io/).
 
<img src="/docs/main-ui.png" width="100%"/>
 
## Get started
#### Install and run
>Pre-condition: update/install `NodeJS` version to be >= *8.11.1*  
 
1) Install ```codecrumbs``` to *devDependencies* (```yarn add codecrumbs -D```)
2) Run ```codecrumbs -d project-src-dir -e project-src-dir/index.js```. Change parameters to match your project:```-d``` is *directory with source code*, ```-e``` is *entry point file* .
3) Go to [http://localhost:2018](http://localhost:2018/#) in the browser to check it out.

#### CLI
Parameter | Description | Example
--- | --- | ---
```-e```, ```--entry``` | Path to project source entry point file | ```-e src/app.js```
```-d```, ```--dir``` | Path to project source code directory | ```-d src```
```-p```, ```--port``` | Port for Codecrumbs client (optional, default *2018*) | ```-p 2019```
```-n```, ```--projectName``` | Project name alias (optional, default same as ```-d``` value) | ```-n my-hello-world```
```-f```, ```--parserFallback``` | AST parser fallback, applicable only for JavaScript project, use it when @babel-parse fails (optional, default *false*) | ```-f true```

## Features
#### Breadcrumbs and trail of breadcrumbs

<img src="/docs/live-changes.gif" width="800"/>

Leave breadcrumb in code by writing down a comment: ```//cc:[parameters;]```.

```cc``` (stands for "CodeCrumb") is a prefix which used by the parser; check example of parameters in the table below:  
 
Example | Description | Use case
--- | --- | ---
```//cc:remember place``` | simple breadcrumb, ```remember place``` is a title of our first breadcrumb | Mark an important place to not forget where it was
```//cc:here is bug;well, seems like a bug in logic``` | simple breadcrumb, ```well, seems like a bug in logic``` is details for breadcrumb, separated by ```;``` | Add extra information, will be rendered in popups
```//cc:signin#3;enable route``` | trail of breadcrumbs,```signin``` is the **trail ID**, ```#3``` is order **number of step**, ```enable route``` is a title describing the step. | A sequence of codecrumbs, use to describe some data flow (e.g. user login, or form submit, etc.).
```//cc:signin#1;firebase sign in;+2;do call to firebase with credentials``` | trail of breadcrumbs,```+2``` is number of lines to highlight, separated by ```;``` | Use number of lines to highlight the code related to breadcrumb 

> Note: current version supports single line comments only. 

#### Multi-codebase integration
You might be interested to study connections between several codebases (sub-modules), codecrumbs supports that.
Simply start codecrumbs multiple times (once for each codebase), it all **will be synced in one picture** inside the browser tab.

E.g. for server-client application, go to the source directory for your server code and run `codecrumbs -e your-server-src/index.py -d your-server-src`, same for client `codecrumbs -e src-client/index.js -d src-client`. **Note:** codebases can be located wherever you want, simply run `codecrumbs` for directory you need.  

<img src="/docs/multi-l-c.png" width="100%"/>

#### Multi-language support
Current version supports next programming languages: `javascript`, `typescript`, `python`, `php`, `java`, `c++` (and others which use `//` as a comment :)). Please file an issue to support other language you would like to have.
> Note: In current version only JavaScript uses AST parser to process the code, hence it offers more features (e.g. Dependencies tree) 

#### Export & import (learn and  share your knowledge)
So let’s say you put together some trail of codecrumbs describing some important flow inside the project. How you can share it with others? Simply download the json file of codecrumbs store, send it to the friend, he/she uploads it to the codecrumbs and can see same you just saw!
<img src="/docs/upload-feature-2.gif" width="100%"/>

## Case studies
The tool (codecrumbs) allows us to learn, document and explain a codebase much faster. The ultimate goal is to have many case studies hosting at [https://codecrumbs.io](https://codecrumbs.io/). **The library of projects "explained with codecrumbs", the place for collaborative learning**. More features around that coming soon, stay tuned. 

## Support
**Sponsors**: contact me if you want to become a sponsor ☺️

**Friends**: if you like this project, please, put a :star: or tweet about it. Thanks! 

Any support is very much appreciated! 👍 😘 ❤️ 

## Contribute
When contributing to this repository, please first discuss the change you wish to make via issue, email, or any other method with the [owner](https://github.com/Bogdan-Lyashenko/) of this repository before making a change. Ideas and suggestions are welcome.
To start development environment, clone the repo & run:
```javascript
yarn && yarn start
```

## WIP
Next features are developing:
- **eject codecrumbs** - ability to remove all "breadcrumbs" from source code in "one click"
- **data transferring between cc trail steps** 
- **VS Code extension** - some neat features right inside the code editor. Checkout [the repo here](https://github.com/Bogdan-Lyashenko/vs-code-codecrumbs). 
