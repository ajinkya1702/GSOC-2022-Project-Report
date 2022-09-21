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
      Users will be able see number of hits in the parenthesis before applying a filter
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
    All filter categories are updated after applying an individual filter or more
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
   Users would be able to search using more symbols and signs
- *Methodology:*
    * Using '//' before any reserved character in the searched keyword 

<center>

| Search breaks when searching for a certain string |
| :---:	|
| <img src="assets/gifs/highlight-inscriptions.gif" width="800" height="450"> |
| Search results for "HS 1475(+)" in Free search|

</center>

### 4. search children entities

- *Final outcome:*\
   Search results of all possible sign-readings of input sign-values are returned.
- *Methodology:*
   * Sign names field was added and populated in database.
   * Containerised jtf-lib library in docker to make requests and get response in the framework.
   * Input query was converted to sign-names using jtf-lib and these sign-names along with sign-values are used to perform the search. 

<center>

| Sign Value permutation |
| :---:	|
| <img src="assets/gifs/sign-permutation.gif" width="800" height="450"> |
| All possible sign-readings of input "muk" can be searched with sign-name "MUG". |

</center>

### 5. Search Settings

- *Final outcome:*\
   Search settings can be saved in session and search results will be displayed accordingly. 
- *Methodology:*
   * Used cakePHP sessions to store the search settings and applied it on the search results.


<center>

| Search Settings |
| :---:	|
| <img src="assets/gifs/search-settings.gif" width="800" height="450"> |
| Removed "Museum collections" and "Period" from search results by modifing Search Settings.  |

</center>

### 6. Input flexibility enhancements

- *Final outcome:*\
   Users can search with both UTF-8 and ASCII characters
- *Methodology:*
   * Used UTF8 to ASCII mapping for converting the input into ASCII before performing search.

<center>

| Input flexibility enhancements |
| :---:	|
| <img src="assets/gifs/input-flexibility.gif" width="800" height="450"> |
| UTF-8 input "diš2" yields search results for ASCII format "disz2" |

</center>

### 7. Images and Transliteration Filter

- *Final outcome:*\
   Search results can be filtered w.r.t to Images and Transliteration according to the access of the user.
- *Methodology:*
   * Created new index for "Images" table.
   * Added elasticsearch queries which would filter results according to the access.

<center>

| Images and Transliteration Filter |
| :---:	|
| <img src="assets/gifs/images-filter.gif" width="800" height="450"> |
| Search results filtered having image type as "photo". |

</center>

## To Do (Post GSoC)

* Robust Testing of all newly added features.
* Documentation (User's and Developer's)
* Fixing any bugs that arise from all the implemented features.

## Acknowledgements

Participating in GSoC was a great learning curve for me, I faced alot of challenges in this journey which helped me in learning new skills. I would like to thank my mentors [Vedant Wakalkar](https://www.linkedin.com/in/karna98/) and [Émilie](https://www.linkedin.com/in/epageperron/) for guiding me and helping me throughout my GSoC journey. I shall always be indebted to such a welcoming organisation to help me enhance my coding skills.
