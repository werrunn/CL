# ENGL682 - NLP and AI Communication
Examining AI Guidelines and Approaches in Leading (Technology)
Institutions for Principles of Trustworthiness, Robustness, and Inclusivity

## R Installation and RStudio Environment
Download R from https://www.r-project.org/ on your system OR Download RStudio from https://www.rstudio.com/
(R script can be run on RStudio Cloud without any download OR on Microsoft Azure Notebooks)

## Project Data and Hypotheses
Web published 'AI principles and guidelines' content from leading tech institutions.
Hypothesis(H0): AI themes from Government, Academic, Big Tech institutions are similar.
Ha: There is difference in the core AI themes as communicated by NIST(government) ,The Royal Society(academic), Google(Big Tech Corporate)

##  Project Workflow in RStudio
 R Packages, library, and Code blocks with related RStudio Screenshots
 
 
 # Web Scraping:
#Automated web scraping in R

install.packages("rvest")
install.packages("Rtools")
library(rvest)
library("dplyr")

Store cleaned data in working directory (CSV or Excel Format) on system
#getwd()
#setwd("C:/Users/...")

# Read CSV data or Excel data in R
#install.packages("readxl")
#library(readxl)
#M_AIguidelines <- "C:/....."
#M_AIguidelines_Read <- read_excel(M_AIguidelines)
#View(M_AIguidelines)

![R-Text analysis visuals](https://user-images.githubusercontent.com/87854956/126885737-327869c7-0d70-4385-8ec5-f8834f8b4531.png)

![1  Data-NIST-RS-Google](https://user-images.githubusercontent.com/87854956/126885771-a4ded151-52d0-4b1d-9cad-8c76810660e1.png)

![2  Data-NIST-RS-Google Screenshot 2021-04-26 202333](https://user-images.githubusercontent.com/87854956/126885776-52e670bc-f2e9-4084-b9c4-a3be6282b569.png)

# Clean Text corpus and Generate Wordclouds,Word frequency table

install.packages("tm")  # for text mining
install.packages("SnowballC") # for text stemming
install.packages("wordcloud") # word-cloud generator 
install.packages("RColorBrewer") # color palettes
install.packages("dplyr")
install.packages("wordcloud2")
install.packages("tibble")
intall.packages("tidyverse")
install.packages("tmap")

library(wordcloud)
library(RColorBrewer)
library(wordcloud2)
library(dplyr)
library(tibble)
library(tidyverse)
library(tmap)

as.data.frame(data.corpus, row.names = NULL, optional = FALSE,
              #cut.names = FALSE, col.names = names(x), fix.empty.names = TRUE,
              #stringsAsFactors = default.stringsAsFactors())
data.corpus.clean.tb=  data.corpus.clean %>% 
  tm::TermDocumentMatrix() %>% 
  as.matrix() %>% as.data.frame() %>% 
  tibble::rownames_to_column() %>%
  
 docs = Corpus(VectorSource(data))
 
 data.corpus = data  %>% 
  tm::VectorSource()%>% 
  tm::Corpus()
data.corpus %>% inspect()

data <- data %>%
  tm_map(data, removeNumbers) %>%
  tm_map(removePunctuation) %>%
  tm_map(data, stripWhitespace)
data <- tm_basemap(data, content_transformer("tolower"))
data <- tm_basemap(data, removeWords, stopwords("english"))
dtm <- TermDocumentMatrix(data.corpus) 
matrix <- as.matrix(dtm) 
words <- sort(rowSums(matrix),decreasing=TRUE)
df <- data.frame(word = names(words),freq=words)

myTdm <- as.matrix(TermDocumentMatrix(mydtm))
FreqMat <- data.frame(ST = rownames(myTdm), 
                      #Freq = rowSums(myTdm), 
                      #row.names = NULL)
head(FreqMat, 10)
dplyr::rename(word = 1, freq = 2) %>%
  dplyr::arrange(desc(freq))

wordcloud(words) = df$word, freq = df$freq, min.freq = 1,max.words=200, random.order=FALSE, rot.per=0.35,colors=brewer.pal(8, "Dark2"))

data.corpus =  data.corpus %>%
  tm_map(FUN = content_transformer(tolower)) %>% # Convert the text to lower case
  tm_map(FUN = removeNumbers) %>% # Remove numbers
  tm_map(removeWords, stopwords("english")) %>% # Remove english common stopwords
  tm_map(removeWords, c("will", "let", "ring")) %>%   # Remove words 
  tm_map(removePunctuation) %>%   # Remove punctuations
  tm_map(stripWhitespace)   # Eliminate extra white spaces
dream.corpus.clean %>% tm::inspect()
data.corpus.clean.tb=  data.corpus.clean %>% 
  tm::TermDocumentMatrix() %>% 
  as.matrix() %>% as.data.frame() %>% 
  tibble::rownames_to_column() %>%
  dplyr::rename(word = 1, freq = 2) %>%
  dplyr::arrange(desc(freq))
  


