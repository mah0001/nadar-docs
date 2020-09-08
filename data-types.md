# Data Types

NADA supports the following study/data types:

- [Microdata/Survey](#microdata)
- [Document](#document)
- [Table](#table)
- [Timeseries](#timeseries)
- [Image (IPTC)](#image)
- [Geospatial](#geospatial)
- [Script](#script)

For each data type, there is a JSON schema available. Use the JSON schemas to find out the structure and fields required for each data type. See [API documentation](https://ihsn.github.io/nada-docs/catalog-admin/).

This page lists R equivalent code for constructing the metadata following the JSON format for all data types. 


# Microdata
The microdata study type is based on the Data Documentation Initiative (DDI 2.5) Codebook standard. NADA uses a JSON schema mapping to the DDI elements. The JSON schema documentation is available at [Microdata Schema documentation](https://ihsn.github.io/nada-docs/catalog-admin/#tag/Survey). 

To create a microdata study, metadata is required in a nested JSON format conforming to the microdata schema. For nadar functions, instead of JSON, you can create a nested list object.

## R template for microdata schema

To create a microdata study, use this nested structure to fill in the metadata fields.

```r
metadata=list(
    "repositoryid"= "central",
    "access_policy"= "data_na",
    "published"= 1,
    "overwrite"= "no",
    "doc_desc"= list(
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
        "prod_date"= "string",
        "version_statement"= list(
        "version"= "string",
        "version_date"= "string",
        "version_resp"= "string",
        "version_notes"= "string"
        )
    ),
    "study_desc"= list(
        "title_statement"= list(
        "idno"= "unique-study-idno",
        "title"= "string",
        "sub_title"= "string",
        "alternate_title"= "string",
        "translated_title"= "string"
        ),
        "authoring_entity"= list(
        list(
            "name"= "string",
            "affiliation"= "string"
        )
        ),
        "oth_id"= list(
        list(
            "name"= "string",
            "role"= "string",
            "affiliation"= "string"
        )
        ),
        "production_statement"= list(
        "producers"= list(
            list(
            "name"= "string",
            "abbr"= "string",
            "affiliation"= "string",
            "role"= "string"
            )
        ),
        "copyright"= "string",
        "prod_date"= "string",
        "prod_place"= "string",
        "funding_agencies"= list(
            list(
            "name"= "string",
            "abbr"= "string",
            "grant"= "string",
            "role"= "string"
            )
        )
        ),
        "distribution_statement"= list(
        "distributors"= list(
            list(
            "name"= "string",
            "abbr"= "string",
            "affiliation"= "string"
            )
        ),
        "contact"= list(
            list(
            "name"= "string",
            "affiliation"= "string",
            "email"= "string"
            )
        ),
        "depositor"= list(
            list(
            "name"= "string",
            "abbr"= "string",
            "affiliation"= "string"
            )
        ),
        "deposit_date"= "string",
        "distribution_date"= "string"
        ),
        "series_statement"= list(
        "series_name"= "string",
        "series_info"= "string"
        ),
        "version_statement"= list(
        "version"= "string",
        "version_date"= "string",
        "version_resp"= "string",
        "version_notes"= "string"
        ),
        "bib_citation"= "string",
        "bib_citation_format"= "string",
        "holdings"= list(
        list(
            "name"= "string",
            "location"= "string",
            "callno"= "string",
            "uri"= "string"
        )
        ),
        "study_notes"= "string",
        "study_authorization"= list(
        "date"= "string",
        "agency"= list(
            list(
            "name"= "string",
            "affiliation"= "string",
            "abbr"= "string"
            )
        ),
        "authorization_statement"= "string"
        ),
        "study_info"= list(
        "study_budget"= "string",
        "keywords"= list(
            list(
            "keyword"= "string",
            "vocab"= "string",
            "uri"= "string"
            )
        ),
        "topics"= list(
            list(
            "topic"= "string",
            "vocab"= "string",
            "uri"= "string"
            )
        ),
        "abstract"= "string",
        "time_periods"= list(
            list(
            "start"= "string",
            "end"= "string",
            "cycle"= "string"
            )
        ),
        "coll_dates"= list(
            list(
            "start"= "string",
            "end"= "string",
            "cycle"= "string"
            )
        ),
        "nation"= list(
            list(
            "name"= "string",
            "abbreviation"= "string"
            )
        ),
        "bbox"= list(
            list(
            "west"= "string",
            "east"= "string",
            "south"= "string",
            "north"= "string"
            )
        ),
        "bound_poly"= list(
            list(
            "lat"= "string",
            "lon"= "string"
            )
        ),
        "geog_coverage"= "string",
        "geog_coverage_notes"= "string",
        "geog_unit"= "string",
        "analysis_unit"= "string",
        "universe"= "string",
        "data_kind"= "string",
        "notes"= "string",
        "quality_statement"= list(
            "standard_name"= "string",
            "standard_producer"= "string",
            "standard_compliance_desc"= "string",
            "other_quality_statement"= "string"
        ),
        "ex_post_evaluation"= list(
            "completion_date"= "string",
            "type"= "string",
            "evaluator"= list(
            list(
                "name"= "string",
                "abbr"= "string",
                "role"= "string"
            )
            ),
            "evaluation_process"= "string",
            "outcomes"= "string"
        )
        ),
        "study_development"= list(
        "activity_type"= "string",
        "activity_description"= "string",
        "participants"= list(
            list(
            "name"= "string",
            "affiliation"= "string",
            "role"= "string"
            )
        ),
        "resource"= list(
            "data_source"= list(
            list(
                "source"= "string"
            )
            ),
            "source_origin"= "string",
            "source_char"= "string"
        ),
        "outcome"= "string"
        ),
        "method"= list(
        "data_collection"= list(
            "time_method"= "string",
            "data_collectors"= list(
            list(
                "name"= "string",
                "abbr"= "string",
                "affiliation"= "string"
            )
            ),
            "collector_training"= list(
            "type"= "string",
            "training"= "string"
            ),
            "frequency"= "string",
            "sampling_procedure"= "string",
            "sample_frame"= list(
            "name"= "string",
            "valid_period"= list(
                list(
                "event"= "string",
                "date"= "string"
                )
            ),
            "custodian"= "string",
            "universe"= "string",
            "frame_unit"= list(
                "is_primary"= true,
                "unit_type"= "string",
                "num_of_units"= "string"
            ),
            "reference_period"= list(
                list(
                "event"= "string",
                "date"= "string"
                )
            ),
            "update_procedure"= "string"
            ),
            "sampling_deviation"= "string",
            "coll_mode"= "string",
            "research_instrument"= "string",
            "instru_development"= "string",
            "instru_development_type"= "string",
            "sources"= list(
            "data_source"= list(
                list(
                "source"= "string"
                )
            ),
            "source_origin"= "string",
            "source_char"= "string",
            "source_doc"= "string"
            ),
            "coll_situation"= "string",
            "act_min"= "string",
            "control_operations"= "string",
            "weight"= "string",
            "cleaning_operations"= "string"
        ),
        "method_notes"= "string",
        "analysis_info"= list(
            "response_rate"= "string",
            "sampling_error_estimates"= "string",
            "data_appraisal"= "string"
        ),
        "study_class"= "string",
        "data_processing"= "string",
        "data_processing_type"= "string",
        "coding_instructions"= list(
            "related_processes"= "string",
            "type"= "string",
            "txt"= "string",
            "command"= "string",
            "command_language"= "string"
        )
        ),
        "data_access"= list(
        "dataset_availability"= list(
            "access_place"= "string",
            "access_place_url"= "string",
            "original_archive"= "string",
            "status"= "string",
            "coll_size"= "string",
            "complete"= "string",
            "file_quantity"= "string",
            "notes"= "string"
        ),
        "dataset_use"= list(
            "conf_dec"= list(
            list(
                "txt"= "string",
                "required"= "string",
                "form_url"= "string",
                "form_id"= "string"
            )
            ),
            "spec_perm"= list(
            list(
                "txt"= "string",
                "required"= "string",
                "form_url"= "string",
                "form_id"= "string"
            )
            ),
            "restrictions"= "string",
            "contact"= list(
            list(
                "name"= "string",
                "affiliation"= "string",
                "uri"= "string",
                "email"= "string"
            )
            ),
            "cit_req"= "string",
            "deposit_req"= "string",
            "conditions"= "string",
            "disclaimer"= "string"
        ),
        "notes"= "string"
        )
    ),
    "data_files"= list(
        list(
        "file_id"= "f1",
        "file_name"= "string",
        "description"= "string",
        "case_count"= 0,
        "var_count"= 0,
        "producer"= "string",
        "data_checks"= "string",
        "missing_data"= "string",
        "version"= "string",
        "notes"= "string"
        )
    ),
    "variables"= list(
        list(
        "file_id"= "f1",
        "vid"= "v1",
        "name"= "string",
        "labl"= "string",
        "var_intrvl"= "discrete",
        "var_dcml"= "string",
        "var_wgt"= 0,
        "var_start_pos"= 0,
        "var_end_pos"= 0,
        "var_width"= 0,
        "var_imputation"= "string",
        "var_security"= "string",
        "var_respunit"= "string",
        "var_qstn_preqtxt"= "string",
        "var_qstn_qstnlit"= "string",
        "var_qstn_postqtxt"= "string",
        "var_qstn_ivulnstr"= "string",
        "var_universe"= "string",
        "var_sumstat"= list(
            list(
            "type"= "string",
            "value"= "string",
            "wgtd"= "string"
            )
        ),
        "var_txt"= "string",
        "var_catgry"= list(
            list(
            "value"= "string",
            "label"= "string",
            "stats"= list(
                list(
                "type"= "string",
                "value"= "string",
                "wgtd"= "string"
                )
            )
            )
        ),
        "var_codinstr"= "string",
        "var_concept"= list(
            list(
            "title"= "string",
            "vocab"= "string",
            "uri"= "string"
            )
        ),
        "var_format"= list(
            "type"= "string",
            "name"= "string",
            "value"= "string"
        ),
        "var_notes"= "string"
        )
    ),
    "variable_groups"= list(
        list(
        "vgid"= "string",
        "variables"= "string",
        "variable_groups"= "string",
        "group_type"= "subject",
        "label"= "string",
        "universe"= "string",
        "notes"= "string",
        "txt"= "string",
        "definition"= "string"
        )
    ),
    "additional"= list(
        "key"="value"
    )
)
```



# Document

R variable structure for Document types

```r
metadata=list(
    "repositoryid"= NULL,
    "published"= 1,
    "overwrite"= "no",
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
    "document_description"= list(
    "title_statement"= list(
        "idno"= "document-unique-id",
        "title"= "document title",
        "sub_title"= "string",
        "alternate_title"= "string",
        "abbreviated_title"= "string"
    ),
    "type"= "article",
    "description"= "string",
    "toc"= "string",
    "toc_structured"= list(
        list(
        "id"= "string",
        "parent_id"= "string",
        "name"= "string"
        )
    ),
    "abstract"= "string",
    "notes"= list(
        list(
        "note"= "string"
        )
    ),
    "scope"= "string",
    "ref_country"= list(
        list(
        "name"= "country name",
        "code"= "string"
        ),
        list(
        "name"= "country name 2",
        "code"= "string"
        )
    ),
    "spatial_coverage"= "string",
    "temporal_coverage"= "string",
    "date_created"= "string",
    "date_available"= "string",
    "date_modified"= "string",
    "date_published"= "string",
    "id_numbers"= list(
        "type"= "string",
        "value"= "string"
    ),
    "publication_frequency"= "string",
    "languages"= list(
        list(
        "name"= "string",
        "code"= "string"
        )
    ),
    "license"= list(
        list(
        "name"= "string",
        "uri"= "string"
        )
    ),
    "bibliographic_citation"= "string",
    "chapter"= "string",
    "edition"= "string",
    "institution"= "string",
    "journal"= "string",
    "volume"= "string",
    "issue"= "string",
    "pages"= "string",
    "series"= "string",
    "creator"= "string",
    "authors"= list(
        list(
        "first_name"= "string",
        "initial"= "string",
        "last_name"= "string",
        "affiliation"= "string"
        )
    ),
    "editors"= list(
        list(
        "first_name"= "string",
        "initial"= "string",
        "last_name"= "string",
        "affiliation"= "string"
        )
    ),
    "translators"= list(
        list(
        "first_name"= "string",
        "initial"= "string",
        "last_name"= "string",
        "affiliation"= "string"
        )
    ),
    "contributors"= list(
        list(
        "first_name"= "string",
        "initial"= "string",
        "last_name"= "string",
        "affiliation"= "string"
        )
    ),
    "publisher"= "string",
    "publisher_address"= "string",
    "rights"= "string",
    "copyright"= "string",
    "usage_terms"= "string",
    "security_classification"= "string",
    "access_restrictions"= "string",
    "sources"= list(
        "data_source"= list(),
        "source_origin"= "string",
        "source_char"= "string",
        "source_doc"= "string"
    ),
    "keywords"= list(
        list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
        )
    ),
    "themes"= list(
        list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
        )
    ),
    "topics"= list(
        list(
        "id"= "string",
        "name"= "string",
        "parent_id"= "string",
        "vocabulary"= "string",
        "uri"= "string"
        )
    ),
    "disciplines"= list(
        list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
        )
    ),
    "audience"= "string",
    "mandate"= "string",
    "pricing"= "string",
    "relations"= list(
        list(
        "name"= "string",
        "type"= "isPartOf"
        )
    ),
    "lda_topics"= list(
        list(
        "model_info"= list(
            list(
            "source"= "string",
            "author"= "string",
            "version"= "string",
            "model_id"= "string",
            "nb_topics"= 0,
            "description"= "string",
            "corpus"= "string",
            "uri"= "string"
            )
        ),
        "topic_description"= list(
            list(
            "topic_id"= 1,
            "topic_score"= .01,
            "topic_label"= "label",
            "topic_words"= list(
                list(
                "word"= "string"
                )
            )
            )
        )
        )
    )
    ),
    "tags"= list(
    list(
        "tag"= "string"
    )
    ),
    "files"= list(
    list(
        "file_uri"= "string",
        "format"= "string",
        "location"= "string",
        "note"= "string"
    )
    )
)

```

# Table

R variable structure for Table types

```r
metadata=list(
  "repositoryid"= "string",
  "published"= 0,
  "overwrite"= "no",
  "metadata_information"= list(
    "idno"= "string",
    "producers"= list
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
      "idno"= "string",
      "table_number"= "string",
      "title"= "string",
      "sub_title"= "string",
      "alternate_title"= "string",
      "abbreviated_title"= "string"
    ),
    "id_numbers"= list(
      "type"= "string",
      "value"= "string"
    ),
    "authoring_entity"= list
      list(
        "name"= "string",
        "affiliation"= "string",
        "abbreviation"= "string",
        "uri"= "string"
      )
    ),
    "contributors"= list
      list(
        "name"= "string",
        "affiliation"= "string",
        "abbreviation"= "string",
        "role"= "string",
        "uri"= "string"
      )
    ),
    "publisher"= list
      list(
        "name"= "string",
        "affiliation"= "string",
        "abbreviation"= "string",
        "role"= "string",
        "uri"= "string"
      )
    ),
    "date_created"= "string",
    "date_published"= "string",
    "date_modified"= "string",
    "version"= "string",
    "description"= "string",
    "table_columns"= list
      list(
        "var_name"= "string",
        "label"= "string"
      )
    ),
    "table_rows"= list
      list(
        "var_name"= "string",
        "label"= "string"
      )
    ),
    "table_footnotes"= list
      list(
        "number"= "string",
        "text"= "string"
      )
    ),
    "table_series"= list
      list(
        "name"= "string",
        "maintainer"= "string",
        "uri"= "string",
        "description"= "string"
      )
    ),
    "statistics"= list
      list(
        "value"= "string"
      )
    ),
    "unit_observation"= list
      list(
        "value"= "string"
      )
    ),
    "data_sources"= list
      list(
        "source"= "string"
      )
    ),
    "time_periods"= list
      list(
        "from"= "string",
        "to"= "string"
      )
    ),
    "universe"= list
      list(
        "value"= "string"
      )
    ),
    "ref_country"= list
      list(
        "name"= "string",
        "code"= "string"
      )
    ),
    "geographic_units"= list
      list(
        "name"= "string",
        "code"= "string",
        "type"= "string"
      )
    ),
    "geographic_granularity"= "string",
    "languages"= list
      list(
        "name"= "string",
        "code"= "string"
      )
    ),
    "links"= list
      list(
        "uri"= "string",
        "description"= "string"
      )
    ),
    "publications"= list
      list(
        "title"= "string",
        "uri"= "string"
      )
    ),
    "keywords"= list
      list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
      )
    ),
    "themes"= list
      list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
      )
    ),
    "topics"= list
      list(
        "id"= "string",
        "name"= "string",
        "parent_id"= "string",
        "vocabulary"= "string",
        "uri"= "string"
      )
    ),
    "disciplines"= list
      list(
        "name"= "string",
        "vocabulary"= "string",
        "uri"= "string"
      )
    ),
    "definitions"= list
      list(
        "name"= "string",
        "definition"= "string",
        "uri"= "string"
      )
    ),
    "classifications"= list
      list(
        "name"= "string",
        "version"= "string",
        "organization"= "string",
        "uri"= "string"
      )
    ),
    "rights"= "string",
    "license"= list
      list(
        "name"= "string",
        "uri"= "string"
      )
    ),
    "citation"= "string",
    "confidentiality"= "string",
    "contacts"= list
      list(
        "name"= "string",
        "role"= "string",
        "affiliation"= "string",
        "email"= "string",
        "telephone"= "string",
        "uri"= "string"
      )
    ),
    "notes"= list
      list(
        "note"= "string"
      )
    ),
    "relations"= list
      list(
        "name"= "string",
        "type"= "isPartOf"
      )
    )
  ),
  "files"= list
    list(
      "file_uri"= "string",
      "format"= "string",
      "location"= "string",
      "note"= "string"
    )
  ),
  "tags"= list
    list(
      "tag"= "string"
    )
  ),
  "additional"= list()
)
```




# Time series

R variable structure for Time series

```r
todo
```

## Time series database

```r
todo
```




# Geospatial

R variable structure for Geospatial

```r
todo
```

# Script

R variable structure for Script

```r
todo
```
