# DS Capstone Survival Guide

- [Prerequisites](#prerequisites)
- [Development environment](#development-environment)
- [Use of Unix command-line tools](#use-of-unix-command-line-tools)
- [Languages and libraries](#languages-and-libraries)
- [Common problems and troubleshooting](#common-problems-and-troubleshooting)
- [ShinyApps limits](#shinyapps-limits)
- [Time management and deadlines](#time-management-and-deadlines)
- [Slow Internet Connections](#slow-internet-connections)
- [Useful resources](#useful-resources)
- [General remarks](#general-remarks)

## Prerequisites

- While it is not required basic familiarity with Unix command-line tools can be extremly useful. If names like [`grep`](http://en.wikipedia.org/wiki/Grep), [`sed`](http://en.wikipedia.org/wiki/Sed) or [`wc`](http://en.wikipedia.org/wiki/Wc_%28Unix%29) doesn't mean anything to you it is a good idea to change that.
- You don't have to be an expert in [Natural Language Processing](http://en.wikipedia.org/wiki/Natural_language_processing) but understanding basic concepts and some experience with analyzing unstructured data will give you a serious advantage. If you're familiar with terms like [tokenization](http://en.wikipedia.org/wiki/Tokenization_%28lexical_analysis%29), [n-gram](http://en.wikipedia.org/wiki/N-gram) or [Markov chain](http://en.wikipedia.org/wiki/Markov_chain) you're good to go.
- You don't need a computer science degree to finish this course, but it is useful to understand basic data structures and algorithms. If you are familiar with [Big O notation](http://en.wikipedia.org/wiki/Big_O_notation) and you can analyze time and memory complexity of the operations like `for(i in 1:n) {foo <- c(i, foo)}` or `which(foo == round(runif(1, 1, n)))` you should be fine.

## Development environment

- Keep your development environment as close as it is possible to the target platform. At this point shinyapps.io is using [Ubuntu 12.04](https://wiki.ubuntu.com/PrecisePangolin) with `en_US.UTF-8` locale. You can create similar environment using tools like [Docker](https://www.docker.com/), [Vagrant](https://www.vagrantup.com/) or [VirtualBox](http://virtualbox.org/).
- Create a reproducible R environment ([Packrat](https://rstudio.github.io/packrat/) is your friend) for your project. Dealing with broken dependencies is a painful and time-consuming process.
- If you execute memory/CPU intensive task try to avoid RStudio.

## Use of Unix command-line tools
- Most operations involving identifying 'unique' words or n-grams, and counting them, can take hours in R and just a few seconds/minuts using Unix/Linux pipes.
- If you work on a Windows machine, keep in mind that you can use [Git Bash](https://msysgit.github.io/#bash) for Unix/Linux command-line tools.
- Using Linux/Unix does not mean you have to give up the ideals of reproducible research: the R function `system()` allows you to call OS commands; if you have a Windows machine, you can solve this problem by using cloud services such as [Domino](www.dominodatalab.com) which accept Linux/Unix commands.

## Languages and libraries

- Some libraries are more equal than others. Even if some library looks like a great fit it doesn't mean it can handle amount of data you have to process.
- JVM based libraries (RWeka, OpenNLP) can provide some very useful functions but it comes at a price. In a restricted environment like ShinyApps it can be a deal breaker.
- Some libraries which had beeen proven to be useful: [`stringi`](http://www.rexamine.com/resources/stringi/),  [Hadleyverse](http://adolfoalvarez.cl/the-hitchhikers-guide-to-the-hadleyverse/) tools ([`data.table`](http://cran.r-project.org/web/packages/data.table/index.html) in particular), [`hash`](http://cran.r-project.org/web/packages/hash/index.html).
- Most likely more trouble than it's worth: [`tm`](http://cran.r-project.org/web/packages/tm/index.html), [`RWeka`](http://cran.r-project.org/web/packages/RWeka/index.html). These are good packages but simply not well suited to Capstone specific workload.

## Common problems and troubleshooting

- If you don't know where to start or you are stuck be sure to check fora. To quote [@LaurentFranckx](https://github.com/LaurentFranckx) _they can make the difference between passing and failing_.
- If you ask a question regarding issues with your code, it is wise to provide the [SSCCE](http://sscce.org/) and all the additional information which can be useful (error messages, warnings, `sessionInfo`) to diagnose the problem. Describing [what have you tried](http://whathaveyoutried.com) is always welcome.
- Contrary to popular belief ShinyApps is not a devious trap created only to make your application fail but it is not a forgiving platform either. Even if your application works fine on your own hardware with lots of spare resources it doesn't mean it will behave as well after deployment. Take away message here is [deploy early and often](http://programmer.97things.oreilly.com/wiki/index.php/Deploy_Early_and_Often).
- If your problem concerns a deployed application be sure to provide [an application log](http://shiny.rstudio.com/articles/shinyapps.html#application-logging) and related errors visible in a browser console ([Firefox](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console), [Chrome](https://developer.chrome.com/devtools/docs/console)). You can use [logging](http://cran.r-project.org/web/packages/logging/index.html) package to create custom log messages.
- If you don't understand [R memory management](http://adv-r.had.co.nz/memory.html) you will most likely fail. You can use common monitoring tools, like [htop](http://en.wikipedia.org/wiki/Htop) or more advanced software like [Munin](http://munin-monitoring.org/) to monitor your application. If you see unexpected memory spikes use [lineprof](https://github.com/hadley/lineprof) to find the source of the problem.
- Keep shiny application directory clean. Uploading things like saved R workspace may have unexpected results.
- Double check submitted links especially if you use Rich Text Editor. What you see is not always what you get.
- [locale](http://stat.ethz.ch/R-manual/R-devel/library/base/html/locales.html) matters. `en_US.UTF-8` is usually the best choice.
- Input file encoding matters as well. Be sure to understand how to use encoding parameter when you create [connections](https://stat.ethz.ch/R-manual/R-devel/library/base/html/connections.html) or use [`readLines`](https://stat.ethz.ch/R-manual/R-devel/library/base/html/readLines.html). If you still encounter problems (like embeded nulls) you can always [read and encode raw data](https://github.com/zero323/r-snippets/blob/master/R/read_and_reencode.R).
- [Handle exceptions](http://adv-r.had.co.nz/Exceptions-Debugging.html) and prepare fallback strategy. If there is an easy way to break your application you can be sure reviewers will find it.

## ShinyApps limits
- Manage shiny hours carefully. Archive any apps you don't need. Set the Instance Idle Timeout for a short period, particularly during your testing. Stop the app in the shiny console when you finish a testing session.
- Size of an application deployed using `deployApp` is limited to [100MB](http://www.rstudio.com/faq-items/load-data-apps-shinyapps-io/).
- _Free tier is restricted to [medium size](http://shiny.rstudio.com/articles/shinyapps.html#application-instances)_. In practice it means 512MB RAM at your disposal. Few orders of magnitude more than [the Apollo Guidance Computer](http://en.wikipedia.org/wiki/Apollo_Guidance_Computer) but most likely less than your smartphone. Use it wisely.

## Time management and deadlines

- Don't wait until the last moment to deploy your projects. If anything can go wrong, it will happened a day before deadline. Just ask anyone who finished this specialization.
- Grading weeks tend to be quite intensive and you have to be prepared to deal with some unexpected issues. Long story short don't leave town.

## Slow Internet Connections

## General remarks
- Be civil and try to have fun.
- Word clouds are evil and therefore should be forbidden.
- Using typical NLP pipelines (tokenization -> punctuation removal -> stop words removal -> stemming) is not the best approach. It will bite you sooner or later.

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
 * [Text Retrieval and Search Engines, University of Illinois at Urbana-Champaign](https://www.coursera.org/course/textretrieval).
 * [Introduction to Linux](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-2).
- Other
 * [awesome-R](https://github.com/qinwf/awesome-R) - A curated list of awesome R frameworks, packages and software.
 * [How to make a great R reproducible example?](http://stackoverflow.com/questions/5963269/how-to-make-a-great-r-reproducible-example)
 * [Next word prediction benchmark](https://github.com/jan-san/dsci-benchmark).
 * [Bitbucket](https://bitbucket.org/) - unlimited private Git repositories.
 * [Shinyapps.io Scaling and Performance Tuning](http://shiny.rstudio.com/articles/scaling-and-tuning.html) - should give required knowledge about ShinyApps architecture.

---
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">DS Capstone Survival Guide</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/zero323/ds-capstone-survival-guide" property="cc:attributionName" rel="cc:attributionURL">Maciej Szymkiewicz and Authors </a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
