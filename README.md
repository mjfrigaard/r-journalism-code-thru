NOTES FROM: Data Challenge with Andrew Ba Tran and Hadley Wickham -
2018-08-17
================
Martin Frigaard

``` r
# add this to yaml for pdf
# output: hrbrthemes::ipsum_pdf
knitr::opts_chunk$set(echo = TRUE, 
                      tidy = FALSE,
                      # dev = "cairo_pdf",
                      size = "small",
                      eval = TRUE,
                      warning = FALSE,
                      message = FALSE
                      )
library(hrbrthemes)
library(ggplot2)
library(Cairo)
library(extrafont)
```

    ## Registering fonts with R

``` r
# extrafont::loadfonts()
```

# Overview

This is a ‘code-through’ of the [Google
Hangout](https://www.youtube.com/watch?v=tHszX31_r4s) with Hadley
Wickham from the [tidyverse](https://www.tidyverse.org/) Andrew Ba Tran
from the Washington Post.

Andrew has a great intro to R for Journalism course available
[here](https://journalismcourses.org/), and [Hadley](http://hadley.nz/)
is the Chief Scientist at RStudio.

### Thoughts on useful functions or tips

> Hadley: so one function that’s not that new but this is super helpful
> and not enough people know about is `case_when` so often which you
> basically use if you want instead of doing a bunch of `if_else` nested
> `if_else` statements.

> Hadley: it so it makes it really easy to do complicated
> transformations across multiple variables.

> Hadley: so sometimes if you see people using `if_else` inside of
> `if_else` s you can replace that with one `case_when`.

> Hadley: which is much much easier to understand and so what is the
> best way to give feedback on packages or is it by filing a Github
> issue or tweeting at people.

### Quotes on R language itself

> Hadley: it just still so blows my mind when I started using our weird
> little niche language that only statisticians used and no one else
> never heard about it.

> Hadley: and even in statistics people didn’t really talk about their
> code that much…more about you know the mathematical statistics and
> fitting models and stuff and I how about how you actually did it using
> software.

> Hadley: so it’s been really really exciting for me just to see it
> explode in popularity and to be used in so many different domains.

> Hadley: I particularly enjoy seeing R and in general and quantitative
> thinking and data science skills move out into disciplines that
> traditionally have not been that quantitative.

> Hadley: I think it sort of I think it’s fair to say that most people
> don’t become journalists because they love math and programming, but
> it turns out that those are really useful skills for understanding the
> world and what people are
doing.

### What is what’s your favorite band and what’s the best music to write R?

> Hadley: I don’t know I already have a favorite band that’s
> disappointing I just basically pick some fairly up the poppy playlist
> on Apple music and listen to it it’s my usual technique or if I’m
> trying to you normally if I’m if I’m writing a book or something I
> don’t listen to music or if I do listen to music I pick something
> that doesn’t have English lyrics otherwise it interferes a bit too
> much with thinking but I do we’re also just when I’m card in place and
> pop music something happy come okay
energetic

### Where do you see R going and what would you love to see contributors focus on building or expanding on in the next 5 years particularly in the realm of mapping?

> Hadley: I think for mapping in particular there’s a lot of things
> where the pieces are all there and if you’re really dedicated you can
> take those pieces and assemble them into something amazing. It might
> take you a bunch of Googling and Stack Overflow questions, or banging
> your head against the wall, and so I’m interested in how people take
> these pieces that are annoying and high friction and wrap them up into
> packages and make them easy to use, and document the way they work.

> Hadley: I think that’s one of the neat things about R ecosystem–that
> people are contributing from all these different domains solving all
> of these different problems.

> Hadley: Most the people using our and most people writing packages are
> not professional software developers or software engineers. I think
> this is one of the most awesome things about R, but it can also be one
> of the scariest things, because you’re using code maybe that hasn’t
> been written by someone trained in computer science, but instead by
> someone who is a great social scientist or a great biologist.

> Hadley: and so I think I’m just really excited, one of the things I
> spend a lot of my time is thinking about is how can we help people who
> want to write package our packages upscale, or how can we make it as
> easy as possible to write an R package. And then how can we make sure
> you can learn the smallest amount of software engineering best
> practices, so that you feel confident using the package.

> Hadley: and so they are making sure all these pieces fit together
> really smoothly.

> Hadley: some of you know that me and my team work on these
> \[packages\] directly, and then there’s just this huge ecosystem of
> other packages so I think hopefully, over time, get better and better
> and easier and easier to
use.

### What would be interesting to know more about the possibilities for creating interactive visualizations for web?

> Hadley: I think the easiest way to do those with R is with `plotly`
> package. If you already know how to use `ggplot2`, you can basically
> use the same `ggplot` syntax and then just plotly-fy at the end and
> turn it into an interactive
graphic.

### What do you think are the most common thing data journalists should know when using R?

> Hadley: one of the most important skills that anyone should have
> really is the abilities knowing how to get help.

> Hadley: knowing how to frame your problem to make it as easy as
> possible for other people to help you

> Hadley: the `reprex` package by Jenny Bryan short for a reproducible
> example is basically a package that allows you to take a snippet of
> code and rerun it in a completely independent
session.

### Most R packages are collection of related tools and functions, but can a single project be organized as a package or maximum reproducibility and documentation?

> Hadley: it can be I think it’s probably a good idea although the tools
> at the moment are a little bit fragile and hard to work
with

### Is there a good website where beginners can ask questions about R? Because the answers on Stack Overflow are often too advanced to understand…

> Hadley: the RRtudio community site. So we’re not gonna guarantee that
> you’ll get your question answered but at least there I think you’ll
> find people who will sympathize with you and share their experiences
> and work together to get a
solution.

### Any advice for people who want to learn R but are intimidated because they have no programming experience?

> Hadley: So I think first of all, even people with no programming
> experience, it’s totally possible to learn R. And I think when you
> learn R, it’s easy to get frustrated and think, “oh it’s me I’m just
> not capable of learning this.” But everyone who tries to learn–no
> matter how smart they are, no matter how familiar they are with other
> programming languages–gets frustrated when they get started. So don’t
> let that initial frustration put you off. It happens to absolutely
> everyone and it’s going to happen for a while. But the good news is
> that it gets better over time.

> Hadley: So my first piece of advice is to acknowledge that you’re
> gonna get frustrated and it’s going to be annoying, that happens to
> everyone. I think related to this, is the best thing you can do is
> **find other people you and learn together. Because learning with
> friends just makes it just the whole experience so vastly more
> enjoyable.**

### How did you get into R originally?

> Hadley: I was doing my undergraduate and statistics at the University
> of Auckland, which was a home of R. So pretty much every class in
> statistics class I taught used R. I think I had one that used SAS,
> which I did not enjoy very much.

> Hadley: But they all pretty much used R. I think one of the reasons
> that I got into R, is I had sort of a fairly decent programming
> background. I was also doing my bachelor’s in computer science at the
> same time, and one of the things that I found appealing about R is
> that was so weird and so different to anything I’d used before. But it
> was clearly so useful to this group of people and the weirdness got me
> and got me intrigued and made me want to figure out why is R this way,
> and what makes it special.

-----

# Data Science Challenge

The website being used is
here:

<https://extapps2.oge.gov/201/Presiden.nsf/PAS%20Filings%20by%20Date?OpenView>

These data are in a table, so this is good news.

> Andrew: I would focus on the annual and then 2018.

> Hadley: Let’s dig into one of these \[hyperlinks\] to see; this is a
> PDF that has a bunch of information about this person, who they got
> money from, and where their retirement savings.

> Hadley: Okay so there’s two goals: the first goal is to just get a
> copy of all of these PDFs locally because you can see there’s a bunch
> of them here and ideally you wouldn’t have to go through and click
> through every single one of those. Once we have downloaded them, can
> we figure out how to turn those PDFs into some data that we can
> analyze somehow. When I look at this page I feel fairly certain these
> data look like it’s in a table, which is good news because if you’ve
> got a table full of data it’s much easier to get started.

## STEP 1: Download the page

``` r
library(tidyverse)
library(rvest)
library(XML)
library(xml2)
```

> Hadley: So if you’re scraping anything from the web, it’s good to get
> familiar with the inspector in your web browser. So here’s an
> inspector, and you can see this is just revealing the tree structure
> of HTML. You can see–luckily–this all is in the table.

Check out this example of an HTML inspector
![](https://mdn.mozillademos.org/files/15499/57-html-panel.png)

> Hadley: Okay, so that’s good news. Now I’m gonna have a go at getting
> that table into R. To do that I’m gonna use the `rvest` package.
> Hopefully, I remember how to use this. I’m going to start just by
> scraping this whole HTML …and I’ve forgotten how to use this…yeah,
> it’s giving me a warning about `read_html()`–which don’t seem to
> exist. Which is odd…oh maybe I’m supposed to use `XML` to read HTML
> (use `xml2`). So now I got a copy of this `page` and all I managed to
> do is download it, and so I can access it from
R.

``` r
page <- xml2::read_html("https://extapps2.oge.gov/201/Presiden.nsf/PAS%20Filings%20by%20Date?OpenView")
glimpse(page, 78)
```

    ## List of 2
    ##  $ node:<externalptr> 
    ##  $ doc :<externalptr> 
    ##  - attr(*, "class")= chr [1:2] "xml_document" "xml_node"

Now we can use the `html` table function.

> Hadley: Then because it has a table, my life’s easier, I can use this
> HTML table function. I’m just going to call this **Table**.

``` r
table <- rvest::html_table(page)
# View(table)
class(table)
```

    ## [1] "list"

> Hadley: Okay, so that contained a list which is my table. You can see
> this looks pretty good right now. You can see the day, you can see the
> date, you can see the name of the report, and the Justice it was from.
> So one problem though is that it doesn’t have the link to the HTML.

See that this is a list–use some bracket sub-setting to get the first
item in the list.

``` r
Table <- rvest::html_table(page)[[1]]
# convert to tibble
PFDRTable <- tibble::as_tibble(Table)
PFDRTable %>% dplyr::glimpse(78)
```

    ## Observations: 944
    ## Variables: 5
    ## $ X1 <chr> "09/20/2018", "09/19/2018", "09/18/2018", "09/13/2018", "08/23/2…
    ## $ X2 <chr> "Annual (2018)", "Annual (2018)", "278 Transaction (09/18/2018)"…
    ## $ X3 <chr> "Quarles, Randal K", "Censky, Stephen L.", "Shanahan, Patrick M"…
    ## $ X4 <chr> "Federal Reserve System Board of Governors", "Department of Agri…
    ## $ X5 <chr> "Governor & Vice Chairman for Supervision", "Deputy Secretary", …

> Hadley: I’m going to name these columns, so it’s going to be a little
> bit easier.

Assign some names to the
tibble.

``` r
base::names(PFDRTable) <- c("date", "report", "name", "department", "position")
PFDRTable %>% dplyr::glimpse(78)
```

    ## Observations: 944
    ## Variables: 5
    ## $ date       <chr> "09/20/2018", "09/19/2018", "09/18/2018", "09/13/2018", …
    ## $ report     <chr> "Annual (2018)", "Annual (2018)", "278 Transaction (09/1…
    ## $ name       <chr> "Quarles, Randal K", "Censky, Stephen L.", "Shanahan, Pa…
    ## $ department <chr> "Federal Reserve System Board of Governors", "Department…
    ## $ position   <chr> "Governor & Vice Chairman for Supervision", "Deputy Secr…

## STEP 2: Where do the links end up?

> Hadley: Okay and then the other thing I have to do is I have to figure
> out where all of these links go. So one way of doing that, which I use
> a lot, is this app called selector gadget.

Install the [selector gadget](https://selectorgadget.com/).

> Hadley: When I load selector gadget, what I’m going to do is I’m going
> to click on the thing that I want to extract, it’s going to come up
> with a candidate expression. You can see it’s got some false
> positives, so I’d only want the links in here. I don’t want the links
> at the top, so I can say, ‘don’t pick those’ and then it comes up with
> a new rule, and that rule looks pretty good. So the rule is expressed
> as a CSS selector, which is saying look for something in the HTML that
> has an ID called `index` and then find all of the `a` tags or the link
> tags inside of that.

After clicking on the hyperlink, and clicking on the false positive (in
red), we learn we are looking for the `#index a` html node. Now we add
this to the initial
extract.

``` r
Page <- xml2::read_html("https://extapps2.oge.gov/201/Presiden.nsf/PAS%20Filings%20by%20Date?OpenView")
Page %>% 
    rvest::html_nodes("#index a") %>% 
    rvest::html_attr("href") %>% length()
```

    ## [1] 945

> Hadley: So now in `Page` we can say `html_nodes()`–let’s just see if
> this works–that’s perfect. You can see this is going to extract 942
> links–this goes to me the `a` tag–which has the place of the links to
> the text, and then I want to extract the `href` attribute, which has
> the link.

This returns 945 rows, which is higher than the number of rows in our
table.

``` r
PFDRTable %>% nrow()
```

    ## [1] 944

This means we need a different node to extract with.

> Hadley: Okay so now I have 942 links, but I only have 941 rows in this
> table which is a little sad. It looks I’ve got an extra link
> somewhere…now I bet one of these has two links.

> Hadley: So what I’m going to do is instead of starting with a link…I
> am going to start with the table cells (`#index td a`)…

``` r
Page %>% 
    # this is the same as above
    rvest::html_nodes("#index td a") %>% 
    rvest::html_attr("href") %>% 
    base::length()
```

    ## [1] 945

> Hadley: I don’t want the table cells (`"#index tr"`), I’m going to
> start with the table rows, and hopefully, they’re 941 of those.

``` r
Page %>% 
    # this is the table row
    rvest::html_nodes("#index tr") %>% 
    # get the hyperlink
    rvest::html_node("a") %>% 
    # this is the header reference
    rvest::html_attr("href") %>% 
    base::length()
```

    ## [1] 944

BINGO\! Put these 944 URLs into the tibble. Notice that the entire
piping operation is to generate a single column of urls that can be
added to the `PFDRTable` (that’s why the length had to identical to the
number of rows in the table).

``` r
PFDRTable$url <- Page %>% 
    # this is the table row
    rvest::html_nodes("#index tr") %>% 
    # get the hyperlink
    rvest::html_node("a") %>% 
    # this is the header reference
    rvest::html_attr("href") 
PFDRTable %>% glimpse(78)
```

    ## Observations: 944
    ## Variables: 6
    ## $ date       <chr> "09/20/2018", "09/19/2018", "09/18/2018", "09/13/2018", …
    ## $ report     <chr> "Annual (2018)", "Annual (2018)", "278 Transaction (09/1…
    ## $ name       <chr> "Quarles, Randal K", "Censky, Stephen L.", "Shanahan, Pa…
    ## $ department <chr> "Federal Reserve System Board of Governors", "Department…
    ## $ position   <chr> "Governor & Vice Chairman for Supervision", "Deputy Secr…
    ## $ url        <chr> "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/CC6…

## STEP 3: Check the 2018 reports

Now check the `Annual (2018)` reports with `dplyr::count()`.

``` r
PFDRTable %>%
    dplyr::count(report, sort = TRUE) %>% 
    View()
```

Note that Hadley ***visually inspects the data a lot to verify what he’s
done produced what he was expecting***.

> Hadley: I think Andrew said that we only mostly care about the annual
> report in 2018

> Hadley: One thing I often worry about is sometimes you have a space at
> the end, and there’s no way to see that…yeah you can’t tell if there’s
> a space, so it’s a good idea just to look at it…I’m just going to look
> at all of them and just skim down to see if there are any others that
> maybe I’m going to miss.

> Hadley: let’s just check what they all are…I’m just going to `count`
> them up…

``` r
PFDRTable %>% 
    dplyr::filter(stringr::str_detect(report, "Annual")) %>% 
    dplyr::count(report, sort = TRUE) %>% 
    utils::head(10)
```

    ## # A tibble: 8 x 2
    ##   report            n
    ##   <chr>         <int>
    ## 1 Annual (2016)    53
    ## 2 Annual (2015)    50
    ## 3 Annual (2014)    46
    ## 4 Annual (2013)    43
    ## 5 Annual (2018)    32
    ## 6 Annual (2012)    14
    ## 7 Annual Term      10
    ## 8 Annual (2017)     8

This is a great use of `dplyr::pull()` to check `dplyr::filter()`
results.

``` r
PFDRTable %>% 
    dplyr::filter(report == "Annual (2018)") %>% 
    dplyr::pull(url) %>% 
    utils::head(10)
```

    ##  [1] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/CC6057396B5CBEB88525830F002952B8/$FILE/Randal-K-Quarles-2018-278.pdf"    
    ##  [2] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/94E7D47752213EE48525830E00294FBB/$FILE/Stephen-L-Censky-2018-278.pdf"    
    ##  [3] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/6F0277ABD5BE0DCA8525830800294DF9/$FILE/Lael-Brainard-2018-278.pdf"       
    ##  [4] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/4C821E2D25E73DEF852582F000568CFF/$FILE/Ryan-Zinke-2018-278.pdf"          
    ##  [5] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/FE3E51A62D7D2B05852582F100293AE9/$FILE/Rod-J-Rosenstein-2018-278.pdf"    
    ##  [6] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/DDDA0D112B138EA5852582EC00294821/$FILE/Jefferson-B-Sessions-2018-278.pdf"
    ##  [7] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/B72D7D1FA55C671A852582D8002945C2/$FILE/France-A-Cordova-2018-278.pdf"    
    ##  [8] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/D7C281310C8D1705852582D80029458D/$FILE/Benjamin-S-Carson-Sr-2018-278.pdf"
    ##  [9] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/4BDACABDEF9D34E9852582D40029415B/$FILE/William-B-Long-2018-278.pdf"      
    ## [10] "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/3DC14CE973BE1FBD852582D100294239/$FILE/George-E-Perdue-2018-278.pdf"

> Hadley: So I’m fairly confident that if I do exactly those, I’m going
> to get the right thing.

> Hadley: Okay, so I’ve got all of these and then I could just pull out
> those URLs and now I want to download them somewhere.

Put these into a table.

``` r
Annual2018 <- PFDRTable %>% dplyr::filter(report == "Annual (2018)")
Annual2018 %>% dplyr::glimpse(78)
```

    ## Observations: 32
    ## Variables: 6
    ## $ date       <chr> "09/20/2018", "09/19/2018", "09/13/2018", "08/21/2018", …
    ## $ report     <chr> "Annual (2018)", "Annual (2018)", "Annual (2018)", "Annu…
    ## $ name       <chr> "Quarles, Randal K", "Censky, Stephen L.", "Brainard, La…
    ## $ department <chr> "Federal Reserve System Board of Governors", "Department…
    ## $ position   <chr> "Governor & Vice Chairman for Supervision", "Deputy Secr…
    ## $ url        <chr> "https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/CC6…

#### Hidden gem: the `basename()` function\!

In order to save the files, we need to figure out the names for them.

> Hadley: If I’m going to download them… I’m going to want to come up
> with a file name and so I think just using the same file name here…and
> I think the easiest let’s just try what they’re called…good…yeah I can
> use this `basename()` function which I happen to know
    about.

``` r
base::basename(Annual2018$url) %>% utils::head(5)
```

    ## [1] "Randal-K-Quarles-2018-278.pdf" "Stephen-L-Censky-2018-278.pdf"
    ## [3] "Lael-Brainard-2018-278.pdf"    "Ryan-Zinke-2018-278.pdf"      
    ## [5] "Rod-J-Rosenstein-2018-278.pdf"

Now we can create the directory for these files.

> Hadley: I’m going to put this in the directory called PDFs.

``` r
# put url in its own object
url <- Annual2018$url
# create path
path <- paste0("pdfs/", base::basename(url))
path %>% utils::head()
```

    ## [1] "pdfs/Randal-K-Quarles-2018-278.pdf"    
    ## [2] "pdfs/Stephen-L-Censky-2018-278.pdf"    
    ## [3] "pdfs/Lael-Brainard-2018-278.pdf"       
    ## [4] "pdfs/Ryan-Zinke-2018-278.pdf"          
    ## [5] "pdfs/Rod-J-Rosenstein-2018-278.pdf"    
    ## [6] "pdfs/Jefferson-B-Sessions-2018-278.pdf"

Now we can download the files.

## STEP 4: Download files with `walk2`

Use `purrr:walk2` and `download.file` to download the pdfs.

> Hadley: Now I want to download each one of those
> files..`download.file()` which takes a single URL, and a single
> destination path, and I’ve got a bunch of files, and a bunch of URLs,
> so if you’re looking for one way to solve this would be with a for
> loop.

> Hadley: I’m just going to skip these steps, and I’m going to use this
> function called `map2` . And what `map2` is designed to do, is
> basically take–what I actually want use is something called
> `walk2`–it’s going to take the URLs, the `path`s it’s gonna call
> `download.file()` once for each URL and `path`…and before I do that
> I’m going to create this PDF directory.

``` r
dir.create("pdfs")
purrr::walk2(.x = url, .y = path, .f = download.file)
```

You’ll see a bunch of
    this…

    trying URL 'https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/CC6057396B5CBEB88525830F002952B8/$FILE/Randal-K-Quarles-2018-278.pdf'
    Content type 'application/pdf' length 112551 bytes (109 KB)
    ==================================================
    downloaded 109 KB
    
    trying URL 'https://extapps2.oge.gov/201/Presiden.nsf/PAS+Index/94E7D47752213EE48525830E00294FBB/$FILE/Stephen-L-Censky-2018-278.pdf'
    Content type 'application/pdf' length 51878 bytes (50 KB)
    ==================================================
    downloaded 50 KB

### Quick Question: *When you were designing new families of functions–like highly specific functions in `purrr` –are you developing for defined problem classes or to extend along possible data structures?*

> Hadley: Part of the motivation, is I keep track of little problems
> that seem like they should not feel harder than they should be. I talk
> to people, and they can tell me what they’re struggling with, and so
> that’s part of it knowing what specific problems that need to be
> solved in general.

> Hadley: I spend a lot of takes a long time but before enough problems
> accumulate to figure out what the class of solutions would be, then I
> also read a lot about other programming languages.

> Hadley: I really making little tables–so for example–in this
> case–`map` and `map2`…and `walk`…and then you know sometimes you
> want the output to be a list and sometimes you want the output to look
> more like this…you’ve got `1 argument` that’s changing you’ve got `2
> arguments` are changing, and you have `n arguments` changing…if you
> want a `list`, well that’s gonna be `map`, if you have 2 arguments and
> your data is in a list that’s going to be `n arguments` - and this is
> a `pmap`.

``` 
                list    int
1 argument      map
2 arguments     map2
n arguments     pmap
```

> Hadley: So I construct these little tables and try and make sure every
> cell is filled so thinking about all other possible combinations and
> can we can we solve them all in one fell swoop.

-----

## STEP 5: Dealing with pdfs

Now we need to figure out how to get the data out of the pdfs.

### Quick sidebar to install `tabulizer`.

The package `tabulizer` was giving me a lot of trouble when loading, so
I documented my steps here.

> Hadley: So I’ve downloaded them all, and I have got a bunch of PDFs.
> Now I have the next problem, which is I have 28 PDFs and I need to
> extract some information from them.

> Hadley: So this isn’t my area of expertise, but I did a little
> googling yesterday I think there’s two packages that you should start
> with: the first one is `tabulizer` which is a wrapper around this java
> program, and the other is `pdftools`.

> Hadley: I think you want to start with `tabulizer` because it is
> designed specifically to extract tables out of PDFs, and so if this
> works you’re good.

``` r
# install.packages("tabulizer")
# install.packages("tabulizerjars")
# install.packages("rJava", ,"http://rforge.net")
library(rJava)
library(tabulizer)
library(pdftools)
```

I was getting hung up on this portion because I needed to install some
additional packages (`rJava`, `tabulizerjars`).

I also needed to install `JDK` with homebrew in the terminal.

    $ brew cask install java
    Updating Homebrew...
    ==> Caveats
    This Cask makes minor modifications to the JRE to prevent issues with
    packaged applications, as discussed here:
    
      https://bugs.eclipse.org/bugs/show_bug.cgi?id=411361
    
    If your Java application still asks for JRE installation, you might need
    to reboot or logout/login.
    
    Installing java means you have AGREED to the license at
      https://www.oracle.com/technetwork/java/javase/terms/license/javase-license.html
    
    ==> Satisfying dependencies
    ==> Downloading http://download.oracle.com/otn-pub/java/jdk/11+28/55eed80b163941
    ==> Downloading from http://download.oracle.com/otn-pub/java/jdk/11+28/55eed80b1
    ######################################################################## 100.0%
    ==> Verifying SHA-256 checksum for Cask 'java'.
    ==> Installing Cask java
    ==> Running installer for java; your password may be necessary.
    ==> Package installers may write to any location; options such as --appdir are i
    Password:
    installer: Package name is JDK 11
    installer: Installing at base path /
    installer: The install was successful.
    java was successfully installed!

Then tried install and saw the
    following:

    Make sure you have Java Development Kit installed and correctly registered in R.
    If in doubt, re-run "R CMD javareconf" as root.

So I ran the command using `sudo` privileges.

    $ sudo R CMD javareconf
    Java interpreter : /usr/bin/java
    Java version     : 11
    Java home path   : /Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
    Java compiler    : /usr/bin/javac
    Java headers gen.: /usr/bin/javah
    Java archive tool: /usr/bin/jar
    
    trying to compile and link a JNI program 
    detected JNI cpp flags    : -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/darwin
    detected JNI linker flags : -L$(JAVA_HOME)/lib/server -ljvm
    clang -I"/Library/Frameworks/R.framework/Resources/include" -DNDEBUG -I/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home/include -I/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home/include/darwin  -I/usr/local/include   -fPIC  -Wall -g -O2  -c conftest.c -o conftest.o
    clang -dynamiclib -Wl,-headerpad_max_install_names -undefined dynamic_lookup -single_module -multiply_defined suppress -L/Library/Frameworks/R.framework/Resources/lib -L/usr/local/lib -o conftest.so conftest.o -L/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home/lib/server -ljvm -F/Library/Frameworks/R.framework/.. -framework R -Wl,-framework -Wl,CoreFoundation
    ld: warning: text-based stub file /System/Library/Frameworks//CoreFoundation.framework/CoreFoundation.tbd and library file /System/Library/Frameworks//CoreFoundation.framework/CoreFoundation are out of sync. Falling back to library file for linking.
    
    
    JAVA_HOME        : /Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
    Java library path: $(JAVA_HOME)/lib/server
    JNI cpp flags    : -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/darwin
    JNI linker flags : -L$(JAVA_HOME)/lib/server -ljvm
    Updating Java configuration in /Library/Frameworks/R.framework/Resources
    Done.

Tried the install again, no luck.

Installed the legacy Java recommended on the tabulizer
[website](https://github.com/ropensci/tabulizer).

Found [this issue](https://github.com/rstudio/rstudio/issues/2254) on
github and ran the following again:

    $ sudo R CMD javareconf

Tried again…

``` r
library(rJava)
library(tabulizer)
library(pdftools)
```

SUCCESS\!\!

### Back to the video….

``` r
library(rJava)
library(tabulizer)
library(pdftools)
library(tabulizerjars)
# redifine path as path_1
path_1 <- "pdfs/Alexander-Acosta-2018-278.pdf"
PDFtables <- tabulizer::extract_tables(path_1)
```

All kinds of crazy warnings.

    WARNING: An illegal reflective access operation has occurred
    WARNING: Illegal reflective access by RJavaTools to method java.util.ArrayList$Itr.hasNext()
    WARNING: Please consider reporting this to the maintainers of RJavaTools
    WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
    WARNING: All illegal access operations will be denied in a future release

This is a good place to export our work thus far. Create a directory.

``` r
# fs::dir_ls(".")
dir.create("data")
# fs::dir_ls("data")
dir.create("data/RData")
```

Save a time-stamped version of this data.

``` r
save.image(file = paste0("data/RData/", 
                         base::noquote(lubridate::today()),
                         "-rjournalism_data_challenge.RData"))
# verify
fs::dir_ls("data/RData")
```

    ## data/RData/2018-09-26-rjournalism_data_challenge.RData
    ## data/RData/2018-09-27-rjournalism_data_challenge.RData

Check the new object.

``` r
PDFtables %>% head()
```

    ## [[1]]
    ##       [,1]                                                           
    ##  [1,] "1. Filer's Positions Held Outside United States Government"   
    ##  [2,] "# ORGANIZATION NAME CITY, STATE"                              
    ##  [3,] ""                                                             
    ##  [4,] "1 Florida International University Miami, Florida"            
    ##  [5,] ""                                                             
    ##  [6,] "2 Breakthrough Miami Miami, Florida"                          
    ##  [7,] "3 Gulliver Schools Miami, Florida"                            
    ##  [8,] "4 U.S. Century Bank Miami, Florida"                           
    ##  [9,] ""                                                             
    ## [10,] "5 American Bar Association Commission on Chicago, Illinois"   
    ## [11,] "Hispanic Legal Rights and Responsibilities"                   
    ## [12,] ""                                                             
    ## [13,] "2. Filer's Employment Assets & Income and Retirement Accounts"
    ## [14,] "# DESCRIPTION EIF"                                            
    ## [15,] ""                                                             
    ## [16,] "1 Florida International University N/A"                       
    ## [17,] "2 U.S. Century Bank, 150,000 warrants, $1.50 N/A"             
    ## [18,] "strike price, vested as follows: 100,000 on"                  
    ## [19,] "3/1/16; 50,000 on 3/1/17."                                    
    ## [20,] "3 U.S. Century Bank N/A"                                      
    ## [21,] ""                                                             
    ## [22,] "4 CREF Growth Yes"                                            
    ## [23,] ""                                                             
    ## [24,] "5 CREF Global Equities Yes"                                   
    ## [25,] ""                                                             
    ## [26,] "6 TIAA Traditional Annuity N/A"                               
    ## [27,] ""                                                             
    ##       [,2]               [,3]              [,4]              [,5]    
    ##  [1,] ""                 ""                ""                ""      
    ##  [2,] "ORGANIZATION"     "POSITION HELD"   "FROM"            "TO"    
    ##  [3,] "TYPE"             ""                ""                ""      
    ##  [4,] "University/Colle" "Dean of the"     "7/2009"          "4/2017"
    ##  [5,] "ge"               "College of Law"  ""                ""      
    ##  [6,] "Non-Profit"       "Director"        "2/2017"          "4/2017"
    ##  [7,] "Non-Profit"       "Trustee"         "11/2016"         "4/2017"
    ##  [8,] "Corporation"      "Chair, Board of" "11/2013"         "4/2017"
    ##  [9,] ""                 "Directors"       ""                ""      
    ## [10,] "Professional"     "Chairman"        "8/2015"          "4/2017"
    ## [11,] "Organization"     ""                ""                ""      
    ## [12,] ""                 ""                ""                ""      
    ## [13,] ""                 ""                ""                ""      
    ## [14,] "VALUE"            "INCOME TYPE"     "INCOME"          ""      
    ## [15,] ""                 ""                "AMOUNT"          ""      
    ## [16,] ""                 "Salary (2017)"   "$151,438"        ""      
    ## [17,] "$100,001 -"       ""                "None (or less"   ""      
    ## [18,] "$250,000"         ""                "than $201)"      ""      
    ## [19,] ""                 ""                ""                ""      
    ## [20,] ""                 "Director Fees"   "$23,000"         ""      
    ## [21,] ""                 "(2017)"          ""                ""      
    ## [22,] "$250,001 -"       ""                "None (or less"   ""      
    ## [23,] "$500,000"         ""                "than $201)"      ""      
    ## [24,] "$250,001 -"       ""                "None (or less"   ""      
    ## [25,] "$500,000"         ""                "than $201)"      ""      
    ## [26,] "$50,001 -"        "Interest"        "$1,001 - $2,500" ""      
    ## [27,] "$100,000"         ""                ""                ""

Extract this list into a table.

> Hadley: so I’ve got this object back…I don’t know what type of object
> it is. Whenever that happens to me, I use `str()` or i use
> `View(PDFtables)` or use `View()` until you can see this is a list of
> length one…so that presumably implies that it loaded one table, and
> each table is a matrix so let’s just extract that take a
    look.

``` r
PDFtables[[1]]
```

    ##       [,1]                                                           
    ##  [1,] "1. Filer's Positions Held Outside United States Government"   
    ##  [2,] "# ORGANIZATION NAME CITY, STATE"                              
    ##  [3,] ""                                                             
    ##  [4,] "1 Florida International University Miami, Florida"            
    ##  [5,] ""                                                             
    ##  [6,] "2 Breakthrough Miami Miami, Florida"                          
    ##  [7,] "3 Gulliver Schools Miami, Florida"                            
    ##  [8,] "4 U.S. Century Bank Miami, Florida"                           
    ##  [9,] ""                                                             
    ## [10,] "5 American Bar Association Commission on Chicago, Illinois"   
    ## [11,] "Hispanic Legal Rights and Responsibilities"                   
    ## [12,] ""                                                             
    ## [13,] "2. Filer's Employment Assets & Income and Retirement Accounts"
    ## [14,] "# DESCRIPTION EIF"                                            
    ## [15,] ""                                                             
    ## [16,] "1 Florida International University N/A"                       
    ## [17,] "2 U.S. Century Bank, 150,000 warrants, $1.50 N/A"             
    ## [18,] "strike price, vested as follows: 100,000 on"                  
    ## [19,] "3/1/16; 50,000 on 3/1/17."                                    
    ## [20,] "3 U.S. Century Bank N/A"                                      
    ## [21,] ""                                                             
    ## [22,] "4 CREF Growth Yes"                                            
    ## [23,] ""                                                             
    ## [24,] "5 CREF Global Equities Yes"                                   
    ## [25,] ""                                                             
    ## [26,] "6 TIAA Traditional Annuity N/A"                               
    ## [27,] ""                                                             
    ##       [,2]               [,3]              [,4]              [,5]    
    ##  [1,] ""                 ""                ""                ""      
    ##  [2,] "ORGANIZATION"     "POSITION HELD"   "FROM"            "TO"    
    ##  [3,] "TYPE"             ""                ""                ""      
    ##  [4,] "University/Colle" "Dean of the"     "7/2009"          "4/2017"
    ##  [5,] "ge"               "College of Law"  ""                ""      
    ##  [6,] "Non-Profit"       "Director"        "2/2017"          "4/2017"
    ##  [7,] "Non-Profit"       "Trustee"         "11/2016"         "4/2017"
    ##  [8,] "Corporation"      "Chair, Board of" "11/2013"         "4/2017"
    ##  [9,] ""                 "Directors"       ""                ""      
    ## [10,] "Professional"     "Chairman"        "8/2015"          "4/2017"
    ## [11,] "Organization"     ""                ""                ""      
    ## [12,] ""                 ""                ""                ""      
    ## [13,] ""                 ""                ""                ""      
    ## [14,] "VALUE"            "INCOME TYPE"     "INCOME"          ""      
    ## [15,] ""                 ""                "AMOUNT"          ""      
    ## [16,] ""                 "Salary (2017)"   "$151,438"        ""      
    ## [17,] "$100,001 -"       ""                "None (or less"   ""      
    ## [18,] "$250,000"         ""                "than $201)"      ""      
    ## [19,] ""                 ""                ""                ""      
    ## [20,] ""                 "Director Fees"   "$23,000"         ""      
    ## [21,] ""                 "(2017)"          ""                ""      
    ## [22,] "$250,001 -"       ""                "None (or less"   ""      
    ## [23,] "$500,000"         ""                "than $201)"      ""      
    ## [24,] "$250,001 -"       ""                "None (or less"   ""      
    ## [25,] "$500,000"         ""                "than $201)"      ""      
    ## [26,] "$50,001 -"        "Interest"        "$1,001 - $2,500" ""      
    ## [27,] "$100,000"         ""                ""                ""

Now we call the extraction `Lines`, then convert to tibble named
`Acosta`.

``` r
Lines <- PDFtables[[1]]
Acosta <- tibble::as_tibble(Lines)
Acosta %>% utils::head()
```

    ## # A tibble: 6 x 5
    ##   V1                                   V2           V3         V4    V5   
    ##   <chr>                                <chr>        <chr>      <chr> <chr>
    ## 1 1. Filer's Positions Held Outside U… ""           ""         ""    ""   
    ## 2 # ORGANIZATION NAME CITY, STATE      ORGANIZATION POSITION … FROM  TO   
    ## 3 ""                                   TYPE         ""         ""    ""   
    ## 4 1 Florida International University … University/… Dean of t… 7/20… 4/20…
    ## 5 ""                                   ge           College o… ""    ""   
    ## 6 2 Breakthrough Miami Miami, Florida  Non-Profit   Director   2/20… 4/20…

Sheesh–many tables in a single PDF.

Assign some names to this table.

> Hadley: So here is the first table see you can see this this looks
> promising…you can see we’ve got each cell on the table, and it’s lined
> up…we have this little problem it’s you can see `college university`…
> `colleges` got split up into two lines, but this seems maybe we’ve got
> two tables jammed into this table…this seems…a worthwhile place to
> start.

> Hadley: I’m going to call this Acosta…that’s a terrible idea because I
> will systematically type it wrong every single time..and again I’m
> going to name those variables so it looks the first column is
> organization, (`org`),`type`, and `position` … and so then the next
> thing I want to do I think let’s just view this again. What’s happened
> is I think we’ve actually got multiple tables in here…so I think a
> good place to start is to try and just work on a single table.

``` r
names(Acosta) <- c("org", "type", "position", "from", "to")
Acosta
```

    ## # A tibble: 27 x 5
    ##    org                               type        position     from   to   
    ##    <chr>                             <chr>       <chr>        <chr>  <chr>
    ##  1 1. Filer's Positions Held Outsid… ""          ""           ""     ""   
    ##  2 # ORGANIZATION NAME CITY, STATE   ORGANIZATI… POSITION HE… FROM   TO   
    ##  3 ""                                TYPE        ""           ""     ""   
    ##  4 1 Florida International Universi… University… Dean of the  7/2009 4/20…
    ##  5 ""                                ge          College of … ""     ""   
    ##  6 2 Breakthrough Miami Miami, Flor… Non-Profit  Director     2/2017 4/20…
    ##  7 3 Gulliver Schools Miami, Florida Non-Profit  Trustee      11/20… 4/20…
    ##  8 4 U.S. Century Bank Miami, Flori… Corporation Chair, Boar… 11/20… 4/20…
    ##  9 ""                                ""          Directors    ""     ""   
    ## 10 5 American Bar Association Commi… Profession… Chairman     8/2015 4/20…
    ## # … with 17 more rows

We can start cleaning with `stringr::str_which()`.

> Hadley: So `str_which` is gonna tell me all the lines, and the pattern
> I’m going to look for is `1. Filer's Position`.

The `stringr::str_which()` function lets us index on a particular
string. We can see more about how this works using another `stringr`
function, `stringr::str_detect()`

``` r
# find the string in Acosta
Acosta %>% 
  dplyr::filter(stringr::str_detect(string = org, 
                                    pattern = "1. Filer's Position"))
```

    ## # A tibble: 1 x 5
    ##   org                                           type  position from  to   
    ##   <chr>                                         <chr> <chr>    <chr> <chr>
    ## 1 1. Filer's Positions Held Outside United Sta… ""    ""       ""    ""

``` r
Acosta %>% 
  dplyr::filter(stringr::str_detect(string = org, 
                                    pattern = "2. Filer's Employment"))
```

    ## # A tibble: 1 x 5
    ##   org                                           type  position from  to   
    ##   <chr>                                         <chr> <chr>    <chr> <chr>
    ## 1 2. Filer's Employment Assets & Income and Re… ""    ""       ""    ""

> Hadley: So you know if you’re doing this, there’s no good way…you just
> have to try something, and then see how it works. You’re going to have
> some positives, and you might have some false negatives, but get
> something that works for one document.

``` r
acosta_line_1 <- stringr::str_which(Acosta$org, "1. Filer's Position")
acosta_line_1
```

    ## [1] 1

``` r
acosta_line_2 <- stringr::str_which(Acosta$org, "2. Filer's Employment")
acosta_line_2
```

    ## [1] 13

These two integers can be used to subset the `Acosta` table with
`dplyr::slice()`.

``` r
Acosta %>% slice((acosta_line_1 + 3):(acosta_line_2 - 2))
```

    ## # A tibble: 8 x 5
    ##   org                                type        position     from   to   
    ##   <chr>                              <chr>       <chr>        <chr>  <chr>
    ## 1 1 Florida International Universit… University… Dean of the  7/2009 4/20…
    ## 2 ""                                 ge          College of … ""     ""   
    ## 3 2 Breakthrough Miami Miami, Flori… Non-Profit  Director     2/2017 4/20…
    ## 4 3 Gulliver Schools Miami, Florida  Non-Profit  Trustee      11/20… 4/20…
    ## 5 4 U.S. Century Bank Miami, Florida Corporation Chair, Boar… 11/20… 4/20…
    ## 6 ""                                 ""          Directors    ""     ""   
    ## 7 5 American Bar Association Commis… Profession… Chairman     8/2015 4/20…
    ## 8 Hispanic Legal Rights and Respons… Organizati… ""           ""     ""

> Hadley: And if you’re gonna do this 100% `tidyverse` you could use
> `slice`…huh there might be a bug in `slice` so I’m going to take it a
> different way…I’m just going to use old school subsetting.

``` r
# Acosta %>% dplyr::slice((acosta_line_1 + 3):(acosta_line_2 - 2))
AcostaPosition <- Acosta[(acosta_line_1 + 3):(acosta_line_2 - 2), ]
AcostaPosition
```

    ## # A tibble: 8 x 5
    ##   org                                type        position     from   to   
    ##   <chr>                              <chr>       <chr>        <chr>  <chr>
    ## 1 1 Florida International Universit… University… Dean of the  7/2009 4/20…
    ## 2 ""                                 ge          College of … ""     ""   
    ## 3 2 Breakthrough Miami Miami, Flori… Non-Profit  Director     2/2017 4/20…
    ## 4 3 Gulliver Schools Miami, Florida  Non-Profit  Trustee      11/20… 4/20…
    ## 5 4 U.S. Century Bank Miami, Florida Corporation Chair, Boar… 11/20… 4/20…
    ## 6 ""                                 ""          Directors    ""     ""   
    ## 7 5 American Bar Association Commis… Profession… Chairman     8/2015 4/20…
    ## 8 Hispanic Legal Rights and Respons… Organizati… ""           ""     ""

> Hadley: I think this looks typical when you’re doing data
> analysis…you’re writing code, you jump around quite a bit, and
> that’s fine. The main thing is to get it working, and then come back
> and do another pass through where you comment so you can remember what
> you what you’re doing…and you can come back in the future…but now I
> think we’ve got a decent subset.

## STEP6: Tackling large data analysis/projects

> Hadley: ***I think it’s whenever you’re tackling a big problem like
> this…you should start with ruthlessly narrowing down the problem until
> you can actually solve it.*** So I’m ruthlessly narrowing it down to
> get one single table worth of data, and I seem to have done that, and
> so I was adjusting these offsets here to say basically how many lines
> so I want to trim, and I’m just going to do it–I’m just doing that
> until I don’t see any empty lines at the top or the bottom.

Now we have the table `AcostaPosition` with some of the `to` and `from`
rows missing, and this is because the `type` and `position` columns
occaisionally spill over into the next row (like `University/College`
and `Dean of the College of Law`)

``` r
AcostaPosition
```

    ## # A tibble: 8 x 5
    ##   org                                type        position     from   to   
    ##   <chr>                              <chr>       <chr>        <chr>  <chr>
    ## 1 1 Florida International Universit… University… Dean of the  7/2009 4/20…
    ## 2 ""                                 ge          College of … ""     ""   
    ## 3 2 Breakthrough Miami Miami, Flori… Non-Profit  Director     2/2017 4/20…
    ## 4 3 Gulliver Schools Miami, Florida  Non-Profit  Trustee      11/20… 4/20…
    ## 5 4 U.S. Century Bank Miami, Florida Corporation Chair, Boar… 11/20… 4/20…
    ## 6 ""                                 ""          Directors    ""     ""   
    ## 7 5 American Bar Association Commis… Profession… Chairman     8/2015 4/20…
    ## 8 Hispanic Legal Rights and Respons… Organizati… ""           ""     ""

``` r
AcostaPosition %>% 
  # what is (to == "") doing?
  dplyr::mutate(carryover = (to == "")) %>% 
  # what does this condition produce?
  dplyr::mutate(type2 = base::ifelse(test = carryover,
                                      yes = type,
                                      no = NA)) %>% 
  # how does fill work?
  tidyr::fill(type2, .direction = "up") %>% 
  # can this be done with stringr::str_c?
  dplyr::mutate(type3 = base::paste0(type, type2)) %>% 
  # why do I filter out TRUE carryovers?
  dplyr::filter(!carryover) %>%
  # now look at them all to see what happened
  dplyr::select(carryover, 
                type, 
                type2, 
                type3)
```

    ## # A tibble: 5 x 4
    ##   carryover type             type2        type3                   
    ##   <lgl>     <chr>            <chr>        <chr>                   
    ## 1 FALSE     University/Colle ge           University/College      
    ## 2 FALSE     Non-Profit       ""           Non-Profit              
    ## 3 FALSE     Non-Profit       ""           Non-Profit              
    ## 4 FALSE     Corporation      ""           Corporation             
    ## 5 FALSE     Professional     Organization ProfessionalOrganization
