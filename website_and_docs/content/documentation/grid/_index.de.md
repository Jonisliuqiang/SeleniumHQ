---
title: "Grid"
linkTitle: "Grid"
weight: 9
description: >
  Want to run tests in parallel across multiple machines? Then, Grid is for you.
aliases: 
        [
          "/documentation/de/selenium_installation/installing_standalone_server/",
          "/documentation/de/grid/",
          "/documentation/de/grid/grid_4/",
          "/documentation/de/grid/purposes_and_main_functionalities/"
        ]
---

{{% pageinfo color="warning" %}}
<p class="lead">
   <i class="fas fa-language display-4"></i> 
   Page being translated from 
   English to German. Do you speak German? Help us to translate
   it by sending us pull requests!
</p>
{{% /pageinfo %}}

Selenium Grid allows the execution of WebDriver scripts on remote machines (virtual
or real) by routing commands sent by the client to remote browser instances.
It aims to provide an easy way to run tests in parallel on multiple machines.

Selenium Grid allows us to run tests in parallel on multiple machines,
and to manage different browser versions and browser configurations centrally
(instead of in each individual test).

Selenium Grid is not a silver bullet.
It solves a subset of common delegation and distribution problems,
but will for example not manage your infrastructure,
and might not suit your specific needs.

## Zweck und hauptsächlich genutze Funktionalität

* Central entry point for all tests
* Management and control of the nodes / environment where the browsers run
* Scaling
* Running tests in parallel
* Cross-platform testing
* Load balancing


{{% alert title="Selenium Grid 4" color="primary" %}}
Grid 4 takes advantage of a number of new technologies in order
to facilitate scaling up while allowing local execution.

Selenium Grid 4 is a fresh implementation and does not share the codebase
the previous version had.

To get all the details of Grid 4 components, understand how it works, and how to set
up you own, please browse thorough the following sections.
{{% /alert %}}