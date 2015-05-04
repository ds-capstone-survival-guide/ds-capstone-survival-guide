# DS Capstone Survival Guide

- [Prerequisites](#prerequisites)
- [Development environment](#development-environment)
- [Languages and libraries](#languages-and-libraries)
- [Common problems and troubleshooting](#common-problems-and-troubleshooting)
- [Time management and deadlines](#time-management-and-deadlines)
- [Useful resources](#useful-resources)

## Prerequisites

- while it is not required basic familiarity with Unix command-line tools can be extremly useful. If names like [`grep`](http://en.wikipedia.org/wiki/Grep), [`sed`](http://en.wikipedia.org/wiki/Sed) or [`wc`](http://en.wikipedia.org/wiki/Wc_%28Unix%29) doesn't mean anything to you it is a good idea to change that.
- you don't have to be an expert in [Natural Language Processing](http://en.wikipedia.org/wiki/Natural_language_processing) but understanding basic concepts and some experience with analyzing unstructured data will give you a serious advantage. If you're familiar with terms like [tokenization](http://en.wikipedia.org/wiki/Tokenization_%28lexical_analysis%29), [n-gram](http://en.wikipedia.org/wiki/N-gram) or [Markov chain](http://en.wikipedia.org/wiki/Markov_chain) you're good to go.

## Development environment

- keep your development environment as close as it is possible to the target platform. At this point shinyapps.io is using [Ubuntu 12.04](https://wiki.ubuntu.com/PrecisePangolin) with `en_US.UTF-8` locale. You can create similar environment using tools like [Docker](https://www.docker.com/), [Vagrant](https://www.vagrantup.com/) or [VirtualBox](http://virtualbox.org/).
- create a reproducible R environment ([Packrat](https://rstudio.github.io/packrat/) is your friend) for your project. Dealing with broken dependencies is a painful and time-consuming process.
- if you execute memory/CPU intensive task try to avoid RStudio.

## Languages and libraries

- some libraries are more equal than others. Even if some library looks like a great fit it doesn't mean it can handle amount of data you have to process.
- JVM based libraries (RWeka, OpenNLP) can provide some very useful functions but it comes at a price. In a restricted environment like ShinyApps it can be deal breaker.

## Common problems and troubleshooting

- if you don't know where to start or you are stuck be sure to check fora. To quote [@LaurentFranckx](https://github.com/LaurentFranckx) _they can make the difference between passing and failing_.
- if you ask a question regarding issues with your code, it is wise to provide the [SSCCE](http://sscce.org/) and all the additional information which can be useful (error messages, warnings, `sessionInfo`) to diagnose the problem. Describing [what have you tried](whathaveyoutried.com) is always welcome.
- contrary to popular belief ShinyApps is not a devious trap created only to make your application fail but it is not a forgiving platform either. Even if your application works fine on your own hardware with lots of spare resources it doesn't mean it will behave as well after deployment. Take away message here is [deploy early and often](http://programmer.97things.oreilly.com/wiki/index.php/Deploy_Early_and_Often).
- if you don't understand [R memory management](http://adv-r.had.co.nz/memory.html) you will most likely fail. You can use common monitoring tools, like [htop](http://en.wikipedia.org/wiki/Htop) or more advanced software like [Munin](http://munin-monitoring.org/) to monitor your application. If you see unexpected memory spikes use [lineprof](https://github.com/hadley/lineprof) to find the source of the problem.
- keep shiny application directory clean. Uploading things like saved R workspace may have unexpected results.

## Time management and deadlines

- don't wait until the last moment to deploy your projects. If anything can go wrong, it will happened a day before deadline. Just ask anyone who finished this specialization.

## Useful resources

- Discussion lists and QA sites.
  * [ShinyApps Users Group](https://groups.google.com/forum/#!forum/shinyapps-users) - A great place to ask a question about the ShinyApps platform.
  * [Shiny Users Group](https://groups.google.com/forum/#!forum/shiny-discuss).
  * [Stack Overflow](http://stackoverflow.com/).
- Books
  * [Data Science at the Command Line](http://shop.oreilly.com/product/0636920032823.do).
  * [Advanced R](http://adv-r.had.co.nz/)
- MOOCs
 * [Natural Language Processing, Columbia University](https://www.coursera.org/course/nlangp).
 * [The Analytics Edge,  MITx](https://www.edx.org/course/analytics-edge-mitx-15-071x-0) - Unit 5: Text Analytics in particular.
- Other
 * [awesome-R](https://github.com/qinwf/awesome-R) - A curated list of awesome R frameworks, packages and software.
 * [How to make a great R reproducible example?](http://stackoverflow.com/questions/5963269/how-to-make-a-great-r-reproducible-example)

---
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">DS Capstone Survival Guide</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/zero323/ds-capstone-survival-guide" property="cc:attributionName" rel="cc:attributionURL">Maciej Szymkiewicz and Authors </a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
