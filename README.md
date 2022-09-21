<img src="assets/GSOC.png" align="center">

<h2 align="center">Project Report on "<a href="https://summerofcode.withgoogle.com/programs/2022/projects/Vvp3XmeB">Search Enhancements</a>" </h2>

## About the project

The project mainly focuses on enhancing the Search and improving the code structure for the same in the CDLI framework and adding new features to it using [Elasticsearch](https://www.elastic.co/elasticsearch/) and [CakePHP](https://cakephp.org/).

<i>Proposal</i> : [Search Enhancements](https://docs.google.com/document/d/1N5AqM5AbE7UVa9rax5_KRReH1v9c8lGzWKyVhd26xMc/edit?usp=sharing)\
<i>Contributions to CDLI</i> : [Merge Requests](https://gitlab.com/cdli/framework/-/merge_requests?scope=all&state=all&author_username=ajinkyamorankar03)\
<i>Weekly Blogs</i> : [Blog](https://cdli-gh.github.io/blog/gsoc22/SearchEnhancements/index)

### Objectives and Deliverables

| \# | Objectives                    | Associated Deliverables         | issue(s) | Pull Requests |    Status |
| --- | ----------------------------- | -------------------------------------------- | -------- | -------- | ---- |
| 1 |  Show number of hits in the parenthesis | Users will be able see number of hits in the parenthesis before applying a filter | [#526](https://gitlab.com/cdli/framework/-/issues/526) | [!663](https://gitlab.com/cdli/framework/-/merge_requests/663) |:heavy_check_mark:|
| 2 | Search Filter Problem | Filter categories are updated after applying of filters |[#531](https://gitlab.com/cdli/framework/-/issues/531) | [!663](https://gitlab.com/cdli/framework/-/merge_requests/663) |:heavy_check_mark: |
| 3 | Search breaks when searching for a certain string | Users would be able to use more symbols and signs while searching|[#1067](https://gitlab.com/cdli/framework/-/issues/1067)| [!676](https://gitlab.com/cdli/framework/-/merge_requests/676) | :heavy_check_mark: |
| 4 | search children entities |While searching for a parent, user would be also given child results of the parent searched|[#1035](https://gitlab.com/cdli/framework/-/issues/1035)| [!696](https://gitlab.com/cdli/framework/-/merge_requests/696) | :heavy_check_mark: |
| 5 | Encode Elasticsearch queries using JSON |Re-writing the ElasticSearch queries in an array structure| [#1129](https://gitlab.com/cdli/framework/-/issues/1129) | [!705](https://gitlab.com/cdli/framework/-/merge_requests/705) |:heavy_check_mark: |
| 6 | Extend Free Search | Adding more fields to the search |[#996](https://gitlab.com/cdli/framework/-/issues/996),[#1233](https://gitlab.com/cdli/framework/-/issues/1233) | [!706](https://gitlab.com/cdli/framework/-/merge_requests/706) | :heavy_check_mark: |

## Preview of objectives

### 1. Show number of hits in the parenthesis
  - *Final outcome:*\
      Users will be able see number of hits in the parenthesis before applying a filter.
  - *Methodology:*
      * Used Elasticsearch buckets aggregations to count number of hits in every search.
<center>

| Show number of hits|
| :---:	|
| <img src="assets/gifs/keywords.gif" width="800" height="450"> |
| Search results for "1156" in Keyword's field. |

</center>

### 2. Search Filter Problem 
 - *Final outcome:*\
    All filter categories are updated after applying an individual filter or more.
 - *Methodology:*
     * Used ElasticSearch Buckets to verify the existence of a filter category.  
<center>

| Search Filter Problem |
| :---:	|
| <img src="assets/gifs/fuzzy-ids.gif" width="800" height="450"> |
| Applying 'clay' filter category after searching for "1156" in Free Search|

</center>

### 3. Search breaks when searching for a certain string

- *Final outcome:*\
   Users would be able to search using more symbols and signs.
- *Methodology:*
    * Using '//' before any reserved character in the searched keyword. 

<center>

| Search breaks when searching for a certain string |
| :---:	|
| <img src="assets/gifs/highlight-inscriptions.gif" width="800" height="450"> |
| Search results for "HS 1475(+)" in Free search|

</center>

### 4. search children entities

- *Final outcome:*\
   * Filter categories are updated to show parent-child relationship using "->" symbol. 
   * Results for children entities would also be include when the user searches for a parent.
- *Methodology:*
   * using tables from database to create the required mappings.
   * Then use those mappings to get required results.

<center>

| search children entities |
| :---:	|
| <img src="assets/gifs/sign-permutation.gif" width="800" height="450"> |
| Searching for "stone" to show parent-child relationship |

</center>

### 5. Encode Elasticsearch queries using JSON

- *Final outcome:*\
   ElasticSearch queries are more readable and appendable 
- *Methodology:*
   * Using PHP `json_encode()` to encode the  query which is in array format and then pass to a GET request for expected results from ElasticSearch.


<center>

| Search Settings |
| :---:	|
| <img src="assets/gifs/search-settings.gif" width="800" height="450"> |
| Removed "Museum collections" and "Period" from search results by modifing Search Settings.  |

</center>

### 6. Extend Free Search

- *Final outcome:*\
   More fields to search and hence more results and data for the users.
- *Methodology:*
   * Adding fields using logstash pipeline and then adding them to respective fields

<center>

| Extend Free Search |
| :---:	|
| <img src="assets/gifs/input-flexibility.gif" width="800" height="450"> |
| Search for 'shiny' in free search which is a keyword of a newly added field |

</center>


## To Do (Post GSoC)

* Robust Testing of all newly added features.
* Documentation (User's and Developer's)
* Fixing any bugs that arise from all the implemented features.

## Acknowledgements

Google Summer Of Code 2022 was a challenging and constructive experience. I have learned new technologies and in addition I have understood  the fundamentals of working on a real time Software Project. I would like to thank my mentor [Yashraj Desai](https://www.linkedin.com/in/yashraj-desai-55a78a1a5/) for his guidance. I have learned a lot from him and his methodolgy in guiding me. I also appreciate the help from [Lar Willighaegan](https://www.linkedin.com/in/lars-willighagen/) and [Émilie](https://www.linkedin.com/in/epageperron/) for guiding me and helping me throughout my GSoC journey. I will always be grateful to [CDLI](https://cdli.ucla.edu/) for being such a hospitable organization.
