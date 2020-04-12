# scholarnetwork2

Originaly Developed by Cheng-Jun Wang & Lingfei Wu
Cheng-Jun Wang wangchj04@gmail.com Lingfei Wu wlf850927@gmail.com

modified belgareth
Original instruction and code via https://github.com/chengjun/scholarNetwork


## Installation ##

An initial release of this package is available in this repository (eventually maybe also on CRAN), and can be installed directly using Hadley Wickham's [devtools](http://cran.r-project.org/web/packages/devtools/index.html) package:

```
if(!require("devtools")) install.packages("devtools")
library("devtools")
install_github("pablobarbera/scholarnetwork")
```

## Examples ##

For now, the package consists of two functions, `extractNetwork` and `plotNetwork`, which correspond to the data collection and data visualization steps.

`extractNetwork` wraps the `get_publications` function from the scholar package, which extracts the list of publications on a Google Scholar profile, cleans it, and then parses the results into a format that is more suitable for network analysis: 

- a data frame of __weighted edges__, where each edge is a collaboration in a publication, and the weight is one divided by number of co-authors; and 

- a data frame with __node-level information__, which includes the group resulting from running a walktrap community detection algorithm. 

```r
d <- extractNetwork(id="jGLKJUoAAAAJ", n=500)
str(d)
```
```
List of 2
 $ nodes:'data.frame':	40 obs. of  3 variables:
  ..$ label : chr [1:40] "A Boydstun" "A Valeriani" "A Venetz" "C Roca Cuberes" ...
  ..$ degree: num [1:40] 0.75 1.69 0.75 0.667 1.69 ...
  ..$ group : num [1:40] 11 7 10 8 7 1 3 4 5 13 ...
 $ edges:'data.frame':	106 obs. of  3 variables:
  ..$ node1 : chr [1:106] "P Barberá" "C Vaccari" "K Ackermann" "P Barberá" ...
  ..$ node2 : chr [1:106] "A Boydstun" "A Valeriani" "A Venetz" "A Venetz" ...
  ..$ weight: num [1:106] 0.25 0.31 0.25 0.25 0.25 ...
```
