# Getting started

To use the API, you will need an API key. If you don't have an API key, you can login to your NADA catalog, go to the profile page and generate a key.


## Load nadar package
To use the package, use library function to load the nadar package

```r
library(nadar)
```


## Setup API key and API URL

```r
nadar::set_api_key("d839d838d838d")
nadar::set_api_url("http://example.com/index.php/api")
```


## Make our first API call
To see if you have setup the API key and API URL correctly, make a basic `GET` call. This should return a list of datasets in the catalog.

```r
datasets<-nadar::datasets()
```


