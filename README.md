![GSOC logo](assets/banner.png)

<h1 align="center"> Google Summer of Code 2022 </h1>




<h2 align="center"><i>Project Report on "<a href="https://summerofcode.withgoogle.com/projects/#5200278048997376">Discovery Search And Advanced Search Features</a>" </i> </h2>

## About the project

The project mainly focuses on enhancing the Search and Advanced search features in the CDLI framework and adding new features to it using [Elasticsearch](https://www.elastic.co/elasticsearch/) and [CakePHP](https://cakephp.org/).

<i>Proposal</i> : [Discovery search and advanced search features](https://docs.google.com/document/d/1WEeNnALSUN4yecCbYxuDyMNUMOzkGcev6Dss4XuNydc/edit#)\
<i>Contributions to CDLI</i> : [Merge Requests](https://gitlab.com/cdli/framework/-/merge_requests?scope=all&state=all&author_username=yashrajdesai30)\
<i>Weekly Blogs</i> : [Blog](https://cdli-gh.github.io/blog/gsoc21/discoverSearchAndAdvancedSearchFeatures/index)

Mentor : [Vedant Wakalkar](https://www.linkedin.com/in/karna98/)

### Objectives and Deliverables

| \# | Objectives                    | Associated Deliverables         | issue(s) | Pull Requests |    Status |
| --- | ----------------------------- | -------------------------------------------- | -------- | -------- | ---- |
| 1 |  Add “Ids” and “Keywords” search fields to both simple and advanced search | Users will be able to search for specific keywords, Id/Numbers artifacts | [#314](https://gitlab.com/cdli/framework/-/issues/314) | [!317](https://gitlab.com/cdli/framework/-/merge_requests/317), [!307](https://gitlab.com/cdli/framework/-/merge_requests/307) |:heavy_check_mark:|
| 2 | Implementation of fuzzy queries | Fuzzy queries would yield search results in all search fields|[#593](https://gitlab.com/cdli/framework/-/issues/593) | [!317](https://gitlab.com/cdli/framework/-/merge_requests/317) |:heavy_check_mark: |
| 3 | Port request to Elasticsearch from cURL to HttpClient | Replaced cURL implementation with HTTP Client|[#350](https://gitlab.com/cdli/framework/-/issues/350)| [!338](https://gitlab.com/cdli/framework/-/merge_requests/338) | :heavy_check_mark: |
| 4 | Highlight transliteration sign values in ATF display |The sign values will be highlighted in the full and compact search results page|[#347](https://gitlab.com/cdli/framework/-/issues/347)| [!354](https://gitlab.com/cdli/framework/-/merge_requests/354) | :heavy_check_mark: |
| 5 | Enable search inscription with sign value permutation |When a user will enable this search feature and search for sign values, all possible sign values with matching sign names of the query will be returned| [#596](https://gitlab.com/cdli/framework/-/issues/596) | [!375](https://gitlab.com/cdli/framework/-/merge_requests/375) |:heavy_check_mark: |
| 6 | Search settings integration | Users will be able to save specific configuration of search settings and search results will be displayed accordingly. |[#540](https://gitlab.com/cdli/framework/-/issues/540) | [!332](https://gitlab.com/cdli/framework/-/merge_requests/332) | :heavy_check_mark: |
| 7 | Input flexibility enhancements |Users will have the flexibility to search with both UTF-8 and ASCII characters |[#597](https://gitlab.com/cdli/framework/-/issues/597)|[!375](https://gitlab.com/cdli/framework/-/merge_requests/375) |:heavy_check_mark: |
| 8 | Filter search results by RTI Image, Transliterations , 3D Data | Users can apply filters such as RTI Image, Transliterations, 3D Data and get search results | [#136](https://gitlab.com/cdli/framework/-/issues/136) | [!369](https://gitlab.com/cdli/framework/-/merge_requests/369) |:heavy_check_mark: |

## Preview of objectives

### 1. Keywords search
  - *Final outcome:*\
      Keywords search field can internally query all the fields of the database and return results accordingly.
  - *Methodology:*
      * Used Elasticsearch query DSL format in backend.
<center>

| Keyword's search |
| :---:	|
| <img src="assets/gifs/keywords.gif" width="800" height="450"> |
| Search results for "Vorderasiatisches Museum" in Keyword's field. |

</center>

### 2. Fuzzy Id's search
 - *Final outcome:*\
    Id's Search should yield results even if input query is not in exact format.
 - *Methodology:*
     * Processed the input query by applying regex operations before performing search.  
<center>

| Fuzzy Id's search |
| :---:	|
| <img src="assets/gifs/fuzzy-ids.gif" width="800" height="450"> |
| Search yields results even for improper input format "A1169" for Museum Id "OIM A01169" in Id's search |

</center>

### 3. Highlight inscriptions

- *Final outcome:*\
   Highlight the inscription input in search results.
- *Methodology:*
    * The text in the inscription field of each search result was processed using regex so that it can highlight the input query. 

<center>

| Highlight inscriptions |
| :---:	|
| <img src="assets/gifs/highlight-inscriptions.gif" width="800" height="450"> |
| Highlights the inscription input "muk" in search results |

</center>

### 4. Sign Value permutation

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

## Acknowledgements

Participating in GSoC was a great learning curve for me, I faced alot of challenges in this journey which helped me in learning new skills. I would like to thank my mentors [Vedant Wakalkar](https://www.linkedin.com/in/karna98/) and [Émilie](https://www.linkedin.com/in/epageperron/) for guiding me and helping me throughout my GSoC journey. I shall always be indebted to such a welcoming organisation to help me enhance my coding skills.
