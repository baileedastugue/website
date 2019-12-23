---
categories:
- RStudio
description: project 2
draft: false
image: images/featured-post/post-3.jpg
tags:
- RSudio
- New
title: Devendra Banhart ft. Python and Reticulate
type: "featured"
---

__The code in its entirety can be found (via RMarkdown) [here](/Project3)__

I highly recommend listening to the song [here](https://open.spotify.com/track/5GiygyFRSZ2jey4almSmrL?si=me44b-c-Syu-_I8yRy6EjQ) while you read the nonsense above.

*pls exclude the following code I am playing around with output atm*


```{include = FALSE}
library(readr)
lexi <- read_csv("~/desktop/website/content/blog/lexi.csv")
library(reticulate)
library(dplyr)
library(tidyr)
library(tidyverse)
lexi1 <- lexi %>% rename(word = Word) %>% rename(conn = connotation) %>% glimpse()
lexi2 <- lexi1 %>% separate(word, into = c("word", "type"), sep = "_") %>% mutate_if(is.character, as.factor) %>% glimpse()
shabop <- paste(read_lines("shabop.txt"), collapse = " ")
```

```{python, include = FALSE}
import re
shabop2 = re.sub(r"[.—,;'\")()?-]","",r.shabop)
shabop3 = re.split(r" +", shabop2)
lower_list=[] #empty list
for word in shabop3:
  temp = word.lower()
  lower_list.append(temp)
counts = {}
for c in lower_list:
    if c in counts:
        counts[c]+=1
    else:
        counts[c]=1
list = []
for c in counts:
   new = (c, counts[c])
   list.append(new)
```

