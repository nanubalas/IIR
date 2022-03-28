# Intelligent Information Retrieval

Abstract:
This project is divided into two tasks. Task one is about building a vertical search engine and task two is about developing a document clustering system. The aim of this project’s task one is to build a vertical 
search engine similar to Google Scholar, but oriented on extracting just papers/books published by members at Coventry University's School of Life Sciences. A vertical search engine is indeed a search engine that is focused on a certain topic. Vertical is commonly used in sales and economics to signify "narrow" or "only one," identical to how the phrase is used for different verticals. Vertical search engines are a sort of vertical gateway since they include data on a certain topic in their indexes. In order to build a vertical search engine we need to crawl the data which means handling with enormous data sets necessitates the development of crawlers capable of crawling to the lowest levels of web pages. Crawlers create indexes based on breadth first. The goal is to start at the original page and follow all of the links there, then repeat. Crawlers can also employ Depth First Traversal, however the benefit of Breadth First Traversal is that the depth or layers of the created tree can be restricted. In this project crawling is done using breadth first search and stored the data in the form lists in different variables. Before indexing the data, did some preparation, such as converting the data to lower case, eliminating punctuation, removing English stop words, and tokenizing the text. After preprocessing the data inverted index need to be created. A mapping between content, such as words or numbers, to their places in a document or series of documents is stored in an inverted index data structure. It's a hashmap-like data structure that guides you from a word to a text or a web page. Now user input is read from the console and applied the same preprocessing techniques and fetched the required data. Document clustering is the unsupervised classification of documents into groups in which documents within a cluster are similar, but documents in different clusters are not. Web pages, blog entries, news stories, and other text files are examples of documents. This article details our research into using the K-means method to cluster text content. Stop word elimination is one example of a feature selection approach. K-means clustering is a more stable approach that gives superior results on practically all data sets.

Task 1:
Search engine:
The main objective of this task is to retrieve only papers/books published by a member of the School of Life Sciences (SLS) at Coventry University: https://pureportal.coventry.ac.uk/en/organisations/school-of-life-sciences.
Plan to build a search engine:
While going through the school of life sciences page I observed that we can fetch the data from research outputs tab or Profiles tab. Initially started crawling the data from research outputs tab and found that authors who are not from the school of life sciences are also retrieved while crawling the data. It is becoming harder when following the other procedures too. Hence, preferred profiles tab to fetch the data so that we can get only the authors who are from the school of life sciences and their publications.
Crawler:
In the school of life sciences profiles tab we have 76 profiles which is two pages to crawl the data. BeautifulSoup4 is a Python package that is used to build the web crawler and extract certain portions of the profiles. The certain portions of profiles are Author’s link for now. Once we receive all the links of authors then we can crawl the data of theirs publications. As per the course work problem we need to fetch only articles and papers from the school of life sciences.
Crawling is done based on breadth first search manner. A graph's Breadth-First Search is comparable to a tree's Breadth-First Traversal. The one kink is that, with exception of trees, graphs can have cycles, which means we can end up simultaneously node again. We utilize a Boolean visited array to prevent processing a node multiple times. For the sake of simplicity, all vertices are believed to be accessible from the initial vertex. 
Initially all the links of authors is taken as list and then publications is attached to each authors link and fetched their publications. In this way we can only fetch the data of authors and their publications which are only from the school of life sciences. The fetched data includes the author’s link, title of the publication, publication link, all the authors who worked on that article or paper, and publication date. The fetched data is stored in the form of lists in different variables.
Beautiful Soup:
Beautiful Soup is a Python package for parsing HTML and XML files and extracting data. It integrates with your preferred parser to offer fluent navigation, search, and modification of the parse tree. It is normal for programmers to save hours or even days of effort.
There were no problems discovered when the python package beautifulsoup4 was evaluated for security flaws and invalid licenses. As a result, the package was judged safe for usage.

Pre-Processing Data:
Once the data is fetched it needs some data preprocessing. Pre-processing is the process of transforming data into a format that a computer can interpret. Filtering out worthless data is one of the most common types of pre-processing. Here the data preprocessing consists of lower case conversion, removing the punctuations, removing the stop words of English language, and tokenizing the text.
Lower case:
All the titles of publications which are stored in the list are converted to lower case using lower function in python.
Removal of Punctuations:
Now the lower cased titles are containing some punctuations, these punctuations are need to be removed and it is done.
Removal of stopwords:
Stopwords are used in computational linguistics to refer to meaningless words. A stopword is a regularly used term that a search engine is intended to ignore; both while indexing items for searching and when retrieving them as the result of a search query.
We don't want these terms to eat up important computation or clutter up in our data. We can simply eliminate them by keeping a list of terms that you regard to be stop words. In Python, the NLTK (Natural Language Toolkit) contains a list of stopwords in 16 different languages. They are located in the nltk data directory. In this project we need to removal only English language.
Tokenizing the text:
Tokenization is the process of breaking down a phrase, sentence, paragraph, or even an entire text document into smaller components like individual words or phrases. Tokens are the names given to each of these smaller units. To visualise this term, look at the image below: Words, numerals, or punctuation marks might be used as tokens.
Using word_tokenize we will tokenize the text.
Inverted Index:
A mapping from content, such as words or numbers, to their places in a document or series of documents is stored in an inverted index data structure. It's a hashmap-like data structure that guides you from a word to a text or a web page.
We'll develop a Word level inverted index, which will return a list of lines that include the word. We'll also make a dictionary, with key values corresponding to the words in the file and the dictionary's value corresponding to the list of line numbers in which they appear.
User’s Input and retrieving the data:
While taking the users input we take it as sentence in the console and do all the preprocessing stuff and retrieve the related data.
I followed all the above mentioned data preprocessing approaches again to process the input data.
Now the final preprocessed data will be fetching the values of inverted index and stored in a list.
Usually any search engine returns the most relevant data at the top and the following other will be the other relevant data.
In this project we will also be showing the results of most relevant data at the top and least relevant data will be followed to the most relevant data.
Finding the most relevant data:
The inverted index which are common for all the words in a sentence are taken first and pushed to the results and follows with the unique inverted index as they are the least relevant data.

Task 2:
Document Clustering:
Descriptors and descriptor extraction are used in document clustering. Descriptors are groups of words that characterise the cluster's contents. Document clustering is commonly thought of as a centralised procedure. Web document clustering for search users is one example of document clustering.
The use of document clustering may be divided into two categories: online and offline. When compared to offline apps, online applications are frequently hampered by efficiency issues. Text clustering may be used for a variety of purposes, including grouping related documents and analysing customer/employee feedback, as well as identifying relevant implicit subjects throughout all texts.
K-means:
k-means clustering is a vector quantization approach that seeks to split n observations into k clusters, with each observation belonging to the cluster with the nearest mean, which serves as the cluster's prototype. As a result, the data space is partitioned into Geometric cells. Within-cluster variances are minimised by k-means clustering, but regular Euclidean distances are not, which is the more difficult Weber problem: the mean optimises squared errors, while only the geometric median reduces Squared euclidean.
Porter Stemming:
The Porter stemming algorithm is a method for eliminating morphological and inflexional ends from English words. Its primary use is in the term normalisation process, which is typically performed while implementing Information Retrieval systems.
Vectorization:
To use textual data for predictive modelling, the text must first be processed to eliminate specific terms, a process known as tokenization. These words must then be converted to integers or floating-point numbers in order to be used as inputs in machine learning methods. Feature extraction or vectorization is the term for this procedure.
TF-IDF:
Term Frequency Inverse Document Frequency is abbreviated as TF-IDF. This is a typical approach for converting text into a meaningful numerical representation, which is then used to fit a machine learning algorithm for prediction.
Procedure:
I took 100 different sentences from BBC news and sports manually and created 100 different text documents(.txt). Using python I read all the data from that 100 documents and stored in a list.
Removed all stopwords from that list and tokenized the entire list using porter stemmer. Performed TF-IDf to convert all the text into a meaningful numerical representation. Performed K-means Clustering and created a model.
Prediction:
Though K-means is mostly used for document clustering rather than classification, the results may nevertheless be used to categorise incoming text documents.
 
The same preprocessing tasks to these arriving documents as we did to the first input documents.
 
References:

V. K. Singh, N. Tiwari and S. Garg, "Document Clustering Using K-Means, Heuristic K-Means and Fuzzy C-Means, " 2011 International Conference on Computational Intelligence and Communication Networks, 2011, pp. 297-301, doi: 10.1109/CICN.2011.62.
2021. [online] Available at: <https://whatis.techtarget.com/definition/vertical-search-engine https://www.promptcloud.com/blog/data-scraping-vs-data-crawling/ https://www.geeksforgeeks.org/applications-of-breadth-first-traversal/ https://www.geeksforgeeks.org/create-inverted-index-for-file-using-python/ https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/ https://www.geeksforgeeks.org/removing-stop-words-nltk-python/ https://www.analyticsvidhya.com/blog/2019/07/how-get-started-nlp-6-unique-ways-perform-tokenization/ https://www.geeksforgeeks.org/create-inverted-index-for-file-using-python/ https://stackoverflow.com/questions/42407976/how-to-load-multiple-text-files-from-a-folder-into-a-python-list-variable https://en.wikipedia.org/wiki/Document_clustering https://en.wikipedia.org/wiki/K-means_clustering https://tartarus.org/martin/PorterStemmer/ https://www.educative.io/edpresso/countvectorizer-in-python> [Accessed 29 November 2021]. 
