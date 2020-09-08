# Manage catalog

## Create new study

### Microdata

The microdata studies are based on the DDI 2.5 codebook. See the [API documentation](https://ihsn.github.io/nada-docs/catalog-admin), for field level documentation. 

Parameters

- idno: `Unique ID for the study`
- repositoryid: `Study collection ID`,
- access_policy: `Data access type` - valid values: [direct, open, public, licensed, remote, data_na], see [data access types](reference#data-access-types)
- data_remote_url: `Link to the repository where data is available for download`
- published: `Set publish status` - valid values: [0=draft, 1=publish]
- overwrite: `Overwrite if a study already exists?` - valid values: ['yes', 'no']
- metadata: `Nested R list based on the Microdata JSON schema` - [Microdata type](data-types#microdata)
- thumbnail: `Path to the thumbnail file`


```r
create_survey(idno, repositoryid, access_policy, data_remote_url,...)
```


#### Example - Create microdata study with basic fields

```r

    metadata=list(
        doc_desc=list(
            "idno"="doc-idno",
            "producers"=list(
                list(
                    "name"="name here",
                    "abbr"="abbreviation"
                )
            )
        ),
        study_desc=list(
            "title_statement"= list(
                "idno"= "survey-idno-test",
                "title"= "Example study title",
                "sub_title"= "study subtitle",
                "alternate_title"= "alternate title",
                "translated_title"= "translated title"
            ),
            "study_info"=list(
                "coll_dates"= list(
                    list(
                        "start"="2019",
                        "end"="2020"
                    )
                ),
                "nation"=list(
                    list(
                        "name"="Afghanistan",
                        "abbreviation"="afg")
                    )
                )
            )
        )
    )


    create_survey (
        idno="survey-idno-test",
        type="survey",
        published = 1,
        overwrite = "yes",
        metadata= metadata,
        thumbnail="path/to/image/thumbnail.png"
    )

```


#### Import DDI
Upload a DDI for creating a microdata study

Parameters

- xml_file: `Path to the DDI2 codebook xml file`
- rdf_file: `Dublin core RDF file for importing external resources`
- repositoryid: `Study collection ID`,
- access_policy: `Data access type`,
- data_remote_url: `Link to the repository where data is available for download`,
- published: `Set the publish status for the study. allowed values are {0=draft, 1=publish}`,
- overwrite: `Set it to yes if you want to replace the study if it already exists. allowed values {yes, no}`,

function: `import_ddi()`

Example:

```r
nadar::import_ddi(
            xml_file="path/to/study-ddi.xml",
            rdf_file="path/to/study-resources.rdf",
            repositoryid="central",
            overwrite="no",
            published=1
)
```



### Documents

To create documents, use the schema fields

JSON Schema document - https://ihsn.github.io/nada-docs/catalog-admin/#operation/createDocument


Parameters

- idno: `Unique ID for the study`
- metadata: `Metadata structure using the document schema`
- repositoryid: `(optional) Study collection ID`,
- access_policy: `(optional) Data access type`,
- data_remote_url: `(optional) Link to the repository where data is available for download`,
- published: `Set the publish status for the study. allowed values are {0=draft, 1=publish}`,
- overwrite: `Set it to yes if you want to replace the study if it already exists. allowed values {yes, no}`,
- thumbnail: `Path to the thumbnail image`

Function: `create_document()`

Example:

```r
metadata=list(
    "document_description"= list(
        "title_statement"= list(
            "idno"= "example-document-idno",
            "title"= "Example document title",
        ),
        "type"= "article",
        "description"= "string",
        "ref_country"= list(
            list(
            "name"= "United states",
            "code"= "USA"
            )
        ),
        "languages"= list(
            list(
            "name"= "English",
            "code"= "EN"
            )
        ),
        "authors"= list(
            list(
            "first_name"= "John",
            "last_name"= "Doe"            
            )
        ),
        "publisher"= "IHSN",
    ),
    "tags"= list(
        list(
            "tag"= "example"
        ),
        list(
            "tag"= "another-tag"
        ),

    ),
    "files"= list(
        list(
            "file_uri"= "path/to/files/file.xls",
            "format"= "application/excel"
        )
    )
)

 create_document (
   idno="document-unique-idno",
   published = 1,
   overwrite = "yes",
   metadata = metadata,
   thumbnail ="path/to/images/thumbnail.jpg"
 )
```


### Tables

Parameters

- idno: `Unique ID for the study`
- repositoryid: `Study collection ID`,
- access_policy: `Data access type` - valid values: [direct, open, public, licensed, remote, data_na], see [data access types](reference#data-access-types)
- data_remote_url: `Link to the repository where data is available for download`
- published: `Set publish status` - valid values: [0=draft, 1=publish]
- overwrite: `Overwrite if a study already exists?` - valid values: ['yes', 'no']
- metadata: `Nested R list based on the Microdata JSON schema` - [Microdata type](data-types#microdata)
- thumbnail: `Path to the thumbnail file`

Function: `create_table()`

Example:

```r
    metadata=list(
        "metadata_information"= list(
        "title"= "string",
        "idno"= "string",
        "producers"= list(
            list(
                "name"= "string",
                "abbr"= "string",
                "affiliation"= "string",
                "role"= "string"
                )
        ),
        "production_date"= "string",
        "version"= "string"
        ),
        "table_description"= list(
            "title_statement"= list(
                "idno"= "table-unique-id",
                "title"= "table title",
                "sub_title"= "string",
                "alternate_title"= "string",
                "abbreviated_title"= "string"
            ),
        ),
        "files"= list(
            list(
                "file_uri"= "http://example.com/files/file.xls",
                "format"= "application/excel",
                "location"= "sheet1",
                "note"= "some note"
            )
        )
    )
    
    create_table (
        idno="table-idno",
        published = 1,
        overwrite = "yes",
        metadata = metadata,
        thumbnail ="images/thumbnail.jpg"
    )
```

### Timeseries
### Scripts
### Geospatial



## Upload thumbnail

Upload a thumbnail for a study

Parameters

- idno: `Unique ID for the study`
- thumbnail: `Path to thumbnail image file`

Function: `upload_thumbnail(idno, thumbnail)`

Example:

```r

upload_thumbnail(idno="study-idno", thumbnail="path/to/thumbnail/image.png")

```



## Delete study

Delete a study from the catalog

Parameters

- idno: `Unique ID for the study`

Function: `delete_study(idno)`

Example:

```r

delete_study(idno="study-idno")

```



## Change publish status

Set study publish status to `draft` or `published`

TODO



## Get study metadata

Return study metadata as JSON

TODO



## Replace study

TODO


## Update/replace partial metadata

Update or replace one or multiples fields in the metadata. Create a metadata variable with nested values but only 
fill in the fields that you want to update.

Parameters:

TODO





## Find study by IDNO

Find a study by IDNO, for matching study, most basic information is returned

Parameters

- idno: `Unique ID for the study`

Function: `find_study(idno)`

Example:

```r

find_study(idno="study-idno")

```



# External resources

External resources are the files attached to a study such as the questionnaires, reports, microdata, etc

## List resources

List external resources for a study

Parameters

- idno: `Unique ID for the study`

Function: `list_resources(idno)`

Example:

```r

list_resources(idno="study-idno")

```


## Get Resource info

Get details of a single resource

Parameters

- idno: `Unique ID for the study`
- resource_id: `Resource ID`

Function: `resource_info(idno, resource_id)`

Example:

```r

resource_info(idno="study-idno", resource_id=1234)

```






## Add new resources

Create and upload an external resource for a study

Parameters

- idno: `Unique ID for the study`
- dctype: `Resource document type`
- title: `Resource title`
- dcformat: `Resource file format`
- author: `Author name`
- dcdate: `Date using YYYY-MM-DD format`
- country: `Country name`
- language: `Language or Language code`
- contributor: `Contributor name`
- publisher: `Publisher name`
- rights: `Rights`
- description: `Resource detailed description`
- abstract:  `Resource abstract`
- toc: `Table of contents`
- file_path: `File path for uploading`
- overwrite: `Overwrite if resource already exists` - Accepted values "yes", "no"


Function: `delete_study(idno)`


Example:
```r
create_resource (
        idno="study-idno",
        dctype="Administrive document [doc/adm]",
        title= "Resource title",
        dcformat="Application/pdf",
        author="Author name",
        dcdate="2020/01/01",
        country="USA",
        language="english",
        contributor="contributor name",
        publisher="pubisher name",
        rights="rights",
        description="resource description",
        abstract="abstract",
        toc="table of contents",
        file_path="path/to/file/publication.pdf",
        overwrite="no")
        
```

## Update a resource

To update the resource metadata or uploaded file

function: `update_resource(study_idno, resource_id, ...)`

Parameters

- idno: `Unique ID for the study`
- resource_id: `Resource numeric ID`
- dctype: `Resource document type`
- title: `Resource title`
- dcformat: `Resource file format`
- author: `Author name`
- dcdate: `Date using YYYY-MM-DD format`
- country: `Country name`
- language: `Language or Language code`
- contributor: `Contributor name`
- publisher: `Publisher name`
- rights: `Rights`
- description: `Resource detailed description`
- abstract:  `Resource abstract`
- toc: `Table of contents`
- file_path: `File path for uploading`

Example:

```
update_resource (
        idno="study-idno",
        resource_id="1234",
        title= "Resource title updated",
        dcformat="Application/pdf",
        file_path="path/to/file/publication.pdf")
```


## Import RDF file
Use Dublin Core RDF files to import resources. The RDF file only include the metadata to create resources. To upload the files for entries in the RDF, use the function `upload_resource` after importing the RDF file.

Function: `import_rdf(idno, rdf_file)`

Parameters

- idno: `Unique ID for the study`
- rdf_file: `RDF file path`

Example:

```
import_rdf(idno="study_idno", rdf_file="path/to/resource.rdf")
```


## Upload files

Upload files for external resources. An upload file is not visible or publish until used by an external resource. 

function: `upload_resource(study_idno, file_path, ...)`

Parameters

- idno: `Unique ID for the study`
- file_path: `File to be uploaded`
- resource_id: `(optional) Resource numeric ID if available`

Example:

```
upload_resource(idno="study_idno", file_path="path/to/file/document.pdf")
```


## Delete a resource

function: `delete_resource(study_idno, resource_id)`

Parameters

- idno: `Study Unique ID`
- resource_id: `Resource ID`

Example:

```
delete_resource(idno="study_idno", resource_id=1293)
```



# Searching the catalog

## List all studies



## Search