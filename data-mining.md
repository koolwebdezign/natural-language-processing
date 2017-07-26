# Data Mining - Natural Language Processing
Jack Welch  
July 26, 2017  


```r
# Use cache inside R markdown file
knitr::opts_chunk$set(cache = TRUE)

# Load the tm library
library(tm)

# Load the stringi library
library(stringi)
```

## Course Dataset - from Johns Hopkins University

The dataset that is required to be used as traininig data for this capstone project is located at the following URL.  

* [https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip](https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip)

Since this is a rather large dataset, I have begun by doing a manual download and unzip of this data.  I obtained my dataset on the date of this report.  A copy of my data is located locally on my personal computer in the *data* sub-folder.  Due to file size limitations set by GitHub, I will not be uploading my original data files that I have downloaded from this URL.

## Load the data into R


```r
# Load the Twitter data
twitter <- readLines(con <- file("./data/en_US.twitter.txt"), encoding = "UTF-8", skipNul = TRUE)
close(con)

# Load the Blog data
blogs <- readLines(con <- file("./data/en_US.blogs.txt"), encoding = "UTF-8", skipNul = TRUE)
close(con)

# Load the News data
news <- readLines(con <- file("./data/en_US.news.txt"), encoding = "UTF-8", skipNul = TRUE)
close(con)
```


```r
# Head of Twitter file
head(twitter)
```

```
## [1] "How are you? Btw thanks for the RT. You gonna be in DC anytime soon? Love to see you. Been way, way too long."  
## [2] "When you meet someone special... you'll know. Your heart will beat more rapidly and you'll smile for no reason."
## [3] "they've decided its more fun if I don't."                                                                       
## [4] "So Tired D; Played Lazer Tag & Ran A LOT D; Ughh Going To Sleep Like In 5 Minutes ;)"                           
## [5] "Words from a complete stranger! Made my birthday even better :)"                                                
## [6] "First Cubs game ever! Wrigley field is gorgeous. This is perfect. Go Cubs Go!"
```

```r
# Head of Blogs file
head(blogs)
```

```
## [1] "In the years thereafter, most of the Oil fields and platforms were named after pagan <U+0093>gods<U+0094>."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## [2] "We love you Mr. Brown."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## [3] "Chad has been awesome with the kids and holding down the fort while I work later than usual! The kids have been busy together playing Skylander on the XBox together, after Kyan cashed in his $$$ from his piggy bank. He wanted that game so bad and used his gift card from his birthday he has been saving and the money to get it (he never taps into that thing either, that is how we know he wanted it so bad). We made him count all of his money to make sure that he had enough! It was very cute to watch his reaction when he realized he did! He also does a very good job of letting Lola feel like she is playing too, by letting her switch out the characters! She loves it almost as much as him."
## [4] "so anyways, i am going to share some home decor inspiration that i have been storing in my folder on the puter. i have all these amazing images stored away ready to come to life when we get our home."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## [5] "With graduation season right around the corner, Nancy has whipped up a fun set to help you out with not only your graduation cards and gifts, but any occasion that brings on a change in one's life. I stamped the images in Memento Tuxedo Black and cut them out with circle Nestabilities. I embossed the kraft and red cardstock with TE's new Stars Impressions Plate, which is double sided and gives you 2 fantastic patterns. You can see how to use the Impressions Plates in this tutorial Taylor created. Just one pass through your die cut machine using the Embossing Pad Kit is all you need to do - super easy!"                                                                                    
## [6] "If you have an alternative argument, let's hear it! :)"
```

```r
# Head of News file
head(news)
```

```
## [1] "He wasn't home alone, apparently."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## [2] "The St. Louis plant had to close. It would die of old age. Workers had been making cars there since the onset of mass automotive production in the 1920s."                                                                                                                                                                                                                                                                                                                                                         
## [3] "WSU's plans quickly became a hot topic on local online sites. Though most people applauded plans for the new biomedical center, many deplored the potential loss of the building."                                                                                                                                                                                                                                                                                                                                 
## [4] "The Alaimo Group of Mount Holly was up for a contract last fall to evaluate and suggest improvements to Trenton Water Works. But campaign finance records released this week show the two employees donated a total of $4,500 to the political action committee (PAC) Partners for Progress in early June. Partners for Progress reported it gave more than $10,000 in both direct and in-kind contributions to Mayor Tony Mack in the two weeks leading up to his victory in the mayoral runoff election June 15."
## [5] "And when it's often difficult to predict a law's impact, legislators should think twice before carrying any bill. Is it absolutely necessary? Is it an issue serious enough to merit their attention? Will it definitely not make the situation worse?"                                                                                                                                                                                                                                                            
## [6] "There was a certain amount of scoffing going around a few years ago when the NFL decided to move the draft from the weekend to prime time -- eventually splitting off the first round to a separate day."
```


```r
# Length of Twitter file
length(twitter)
```

```
## [1] 2360148
```

```r
# Length of Blogs file
length(blogs)
```

```
## [1] 899288
```

```r
# Length of News file
length(news)
```

```
## [1] 77259
```



```r
# Longest entry in Twitter file
twitter_i <- stri_length(twitter)
max(twitter_i)
```

```
## [1] 140
```

```r
# Longest entry in Blogs file
blogs_i <- stri_length(blogs)
max(blogs_i)
```

```
## [1] 40833
```

```r
# Longest entry in News file
news_i <- stri_length(news)
max(news_i)
```

```
## [1] 5760
```

