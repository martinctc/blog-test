---
title: "My favourite alternative to Excel dashboards"

author: "Martin Chan"
date: "April 27, 2019"
layout: post
---


<section class="main-content">
<div id="excel-dashboards-are-great-what" class="section level2">
<h2>Excel dashboards are great… what? 😯</h2>
<p>For all the complaints that people have for Excel, it still has many clear, indisputable advantages.</p>
<p>For one, it is extremely <strong>accessible</strong> - almost everyone has Excel installed on their computer. It’s <strong>familiar</strong> to most people, and practically anyone who can use a computer will know how to perform basic operations like doing a SUM function or filter a column.</p>
<p><img src="{{ site.url }}{{ site.baseurl }}/knitr_files/Favourite_Alternative_Excel_26-04-19_files/figure-html/meme-1.png" width="50%" style="float:right; padding:10px" /></p>
<p>In the context of sharing analysis or findings, Excel more importantly has <strong>portability</strong>. By this, I am referring to Excel’s ability to run in a very wide range of circumstances:</p>
<ul>
<li><p>You can send stand-alone Excel files over email, share them with colleagues/clients over SharePoint</p></li>
<li><p>You can open Excel files without internet if you’re stuck in a rainforest or the London Underground (!)</p></li>
<li><p>There is no requirement for additional installed software other than Excel</p></li>
<li><p>There is no need for the dashboard to communicate with a server</p></li>
</ul>
<p>Moreover, Excel files are also virtually <strong>free</strong> to create, as realistically you don’t need to take out any <em>additional</em> licenses in order to create/host a dashboard in Excel, unlike Tableau or Power BI where there is at least some cost for a practical commercial deployment. Its ease of use and wide availability arguably also makes it easier for your team to collaborate on putting a dashboard together.</p>
<div id="advantages-of-excel" class="section level3">
<h3>Advantages of Excel</h3>
<p>Therefore Excel has many advantages then:</p>
<ol style="list-style-type: decimal">
<li>Accessible / Familiarity</li>
<li>Portable</li>
<li>Virtually free</li>
<li>Easier for collaboration <a href="#fn1" class="footnoteRef" id="fnref1"><sup>1</sup></a></li>
</ol>
<p>But do all of these advantages sufficiently justify sticking to Excel when you want to deploy a ‘dashboard’ solution?</p>
<hr />
</div>
</div>
<div id="what-is-a-dashboard" class="section level2">
<h2>What is a dashboard?</h2>
<p>Before I dive into the limits of Excel, there’s a question: what is a dashboard supposed to be anyway?</p>
<p><a href="https://www.gartner.com/it-glossary/dashboard/">Gartner’s IT glossary</a> defines a dashboard as:</p>
<blockquote>
<p><em>… a reporting mechanism that aggregate and display metrics and key performance indicators (KPIs), enabling them to be examined at a glance by all manner of users before further exploration via additional business analytics (BA) tools.</em></p>
</blockquote>
<div class="figure">
<img src="{{ site.url }}{{ site.baseurl }}\images\Dashboard+Course+in+Excel.png" alt="Excel dashboard image from https://www.thesmallman.com/excel-dashboard-course" width="70%" style="float:bottom; padding:10px" />
<p class="caption">
Excel dashboard image from <a href="https://www.thesmallman.com/excel-dashboard-course" class="uri">https://www.thesmallman.com/excel-dashboard-course</a>
</p>
</div>
<p>By a ‘dashboard’ solution however, I’m thinking in terms of a broad, but also minimal definition. A dashboard doesn’t need to be used for displaying KPIs, for one. I’d go for something simple, like:</p>
<blockquote>
<p><em>Dashboard: a collection of visualisations with at least some degree of interactivity, available in a single and typically layered visual space.</em></p>
</blockquote>
<p>(‘Layered’ refers to drop-downs, sheets, pages, tabs, etc.)</p>
<p>One could argue that interactivity is not a requirement for a visualisation dashboard, but I do think where the user can have some control over the data that is shown (e.g. tooltips, hovering effects) does make a dashboard importantly different from say, a PowerPoint slide deck.</p>
<p>Under this broad definition, Excel certainly can provide a <strong>lightweight</strong>, <strong>portable</strong>, <strong>easy-to-setup</strong> dashboard solution for commercial deployment.</p>
<hr />
</div>
<div id="limits-of-excel" class="section level2">
<h2>Limits of Excel</h2>
<p>In my personal experience, the limitations of Excel dashboards come from two main areas:</p>
<ol style="list-style-type: decimal">
<li>the limits of its visualisation capabilities and options, and</li>
<li>the limits of its data analysis capabilities.</li>
</ol>
<p>The first point is straightforward: the visualisations that you can display on an Excel dashboard are limited to the charts that are available through Microsoft Excel. Although you can do most of the things that you might want to do (bar charts, line charts, etc.), more specific features such as network graphs, faceted bar charts, sankey diagrams, and word clouds are practically impossible to create.</p>
<p>The second point of criticism is more around the fact that Excel isn’t simply designed for more complex analysis tasks, such as grouping large number of records (even 10k+), running slightly more complex regression / classification models, or text mining tasks like analysing ngrams. This means that the data contained in the dashboard must be a summarised output created from another software / environment (e.g. R, SAS, SPSS), requiring an additional step between analysis and visualisation. Although it might sound like this is only one additional step, this has implications for <strong>scalability</strong>: if your task is to create 100 of these Excel dashboards, how do you reliably and quickly get the analysis you’ve done in a separate analysis program into Excel? Sounds like a bit of a nightmare! 😨</p>
</div>
<div id="whats-a-good-alternative-then" class="section level2">
<h2>What’s a good alternative then? 🤔</h2>
<p>The ability to perform both <em>analysis</em> and <em>visualisation</em> in a single environment is probably one of the most attractive advantages of <a href="https://shiny.rstudio.com/">Shiny</a>. The fact that it is based in R also means that it is by no means limited (effectively <em>unlimited</em>) in terms of the charting libraries available:</p>
<ul>
<li><a href="https://ggplot2.tidyverse.org/">ggplot2</a></li>
<li><a href="https://cran.r-project.org/web/packages/plotly/index.html">plotly</a></li>
<li><a href="https://hafen.github.io/rbokeh/">rbokeh</a></li>
<li><a href="http://jkunst.com/highcharter/">highcharter</a> (caveat: you need a license if you’re using Highcharts commercially, but otherwise free to use)</li>
<li><a href="https://rstudio.github.io/dygraphs/">dygraphs</a> … to name just a few!</li>
</ul>
<p>I wouldn’t, however, say that <strong>Shiny</strong> is the best alternative to Excel - given the requirements that I need to meet in terms of client deliverables. From my personal experience, where <strong>Shiny</strong> leads on interactivity, it suffers on accessibility and portability. Deploying a Shiny app typically requires hosting through Shiny Server, or through <a href="https://www.shinyapps.io/">shinyapps.io</a>, where the user will require an internet connection for access. Hosting a Shiny app on shinyapps.io with credentials require a hosting fee, unlike Excel which you can encrypt for free. My personal experience is that clients or end-users perceive web apps to be less reliable, as it is dependent on the server / internet connection working properly, whereas Excel files wouldn’t fail in the same way.</p>
</div>
<div id="flexdashboard" class="section level2">
<h2>flexdashboard 🔥</h2>
<p>My favourite alternative actually is <a href="https://rmarkdown.rstudio.com/flexdashboard/">flexdashboard</a>, which is importantly different from Shiny in that it is possible to run itself as a stand-alone static HTML file that doesn’t depend on communicating with a back-end server.</p>
<p>Effectively, this is a single HTML file with interactive features (though not as <em>interactive</em> as Shiny, if that makes sense) that opens up in a browser, and which you can send via email or host securely on SharePoint. You still have access to all the charting libraries that are available in R, as long as the libraries themselves can run without communicating to a server - plenty of examples are available on RStudio’s <a href="http://gallery.htmlwidgets.org/">html widgets gallery</a>. All the production is done in a <a href="https://rmarkdown.rstudio.com/">RMarkdown</a> document which you would use the flexdashboard package in combination with <a href="https://yihui.name/knitr/">knitr</a> to create the static HTML dashboard document.</p>
<p>As <a href="https://datastrategywithjonathan.com/">Jonathan Ng</a> pointed out to me, using the <a href="https://rstudio.github.io/DT/">DT package</a> within flexdashboard means you can add interactive buttons that lets the user download data as Excel, CSV, or PDFs - an incredible interactive feature through static HTML!<a href="#fn2" class="footnoteRef" id="fnref2"><sup>2</sup></a></p>
<p>I’ve also created a demo flexdashboard on my website which I aim to showcase some examples of what you can do with a static HTML dashboard. <a href="https://martinctc.github.io/examples/flexdashboard_example.html">Check it out!</a> I aim to continuously update this as I explore more available HTML widgets.</p>
</div>
<div id="conclusion" class="section level2">
<h2>Conclusion</h2>
<p>Let’s look back at some of the points that we laid out as the strengths of an Excel dashboard solution, and see whether flexdashboard covers them:</p>
<ol style="list-style-type: decimal">
<li><p><strong>Accessible / Familiarity</strong>: YES - it’s safe to assume that most computers, if not all, have internet browsers, in which the HTML dashboard will load properly. Familiarity does come down to the UX design the of the dashboard, but a flexdashboard will generally be intuitive to operate.</p></li>
<li><p><strong>Portable</strong>: YES - you don’t need an internet connection, and static HTML files can easily be sent via email.</p></li>
<li><p><strong>Virtually free</strong>: YES - because there’s no hosting needed, and R itself is free.</p></li>
<li><p><strong>Easier for collaboration</strong> : I’d say YES, on the condition that your team is also familiar with R. The fact that flexdashboards are written in code means that it’s easier for two or more people to be working on the same dashboard at the same time than an Excel file. If done properly, R code is also more readable than Excel cell references.</p></li>
</ol>
<p>So hands down, <strong>flexdashboard</strong> is my favourite alternative to Excel dashboard!</p>
</div>
<div class="footnotes">
<hr />
<ol>
<li id="fn1"><p>This point is debatable, as Excel cell references are not generally considered easy-to-follow, and neither does the nature of spreadsheets make it easy for two or more people to work on the same Excel file at the same time.<a href="#fnref1">↩</a></p></li>
<li id="fn2"><p>See the video tutorial <a href="https://www.youtube.com/watch?v=ux2tQqgY8Gg">here</a><a href="#fnref2">↩</a></p></li>
</ol>
</div>
</section>
