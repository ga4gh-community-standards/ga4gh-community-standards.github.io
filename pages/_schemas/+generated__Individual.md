---
title: 'Individual'
layout: default
permalink: "/schemas/blocks/Individual.html"
excerpt_separator: <!--more-->
category:
  - schemas
tags:
  - code
---
## Individual


#### Status: __proposed__

<!--more-->



#### Provenance


#### Authors

*

#### Schema source: [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/working/individual.yaml)
#### Properties of the _Individual_ class

<table>
  <tr>
    <th>Property</th>
    <th>Type</th>
    <th>Format</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>biocharacteristics</td>
    <td>array</td>
    <td>:&nbsp;<a href="./Phenotype.html">./Phenotype</a></td>
    <td>list of Phenotype objects with properly prefixed term ids, describing features of the individual which are not specific to the reported biosample(s); typical examples here are sex, species and "systemic" phenotypes and diseases
</td>
  </tr>
  <tr>
    <td>created</td>
    <td>timestamp</td>
    <td></td>
    <td>The creation time of this record, in ISO8601
</td>
  </tr>
  <tr>
    <td>data_use_conditions</td>
    <td>:&nbsp;<a href="./Ontology_term.html">./Ontology_term</a></td>
    <td></td>
    <td>Data use conditions applying to data from this individual, as ontology object (e.g. DUO).
</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td></td>
    <td>A free text description of the individual.</td>
  </tr>
  <tr>
    <td>external_references</td>
    <td>array</td>
    <td>:&nbsp;<a href="./Reference.html">./Reference</a></td>
    <td>Different representations of the same record, not different records in relation with this individual
</td>
  </tr>
  <tr>
    <td>geo_provenance</td>
    <td>:&nbsp;<a href="./Geo_location.html">./Geo_location</a></td>
    <td></td>
    <td>This geo_class attribute ideally describes the geographic location of where this individual originates from.
This value may reflect either the place of birth or residence, but frequently may correspond to the place the study was performed.
</td>
  </tr>
  <tr>
    <td>id</td>
    <td>string</td>
    <td></td>
    <td>The local-unique identifier of this individual (referenced as "individual_id").</td>
  </tr>
  <tr>
    <td>info</td>
    <td>:&nbsp;<a href="./Info.html">./Info</a></td>
    <td></td>
    <td>additional variant information, as defined in the example and accompanying documentation TODO this should be its own class</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td></td>
    <td>A short descriptive "name" for the individual, which may or may not correspond to a "real name". Unstructured text.
</td>
  </tr>
  <tr>
    <td>organism</td>
    <td>:&nbsp;<a href="./Ontology_term.html">./Ontology_term</a></td>
    <td></td>
    <td>An NCBI taxonomy term describing the species of the individual.
For resources where there may be more than one organism being studied it is advisable to indicate the taxonomic identifier of that organism, to it's most specific level
</td>
  </tr>
  <tr>
    <td>sex</td>
    <td>:&nbsp;<a href="./Ontology_term.html">./Ontology_term</a></td>
    <td></td>
    <td>A PATO term describing the biological sex of the individual
</td>
  </tr>
  <tr>
    <td>updated</td>
    <td>timestamp</td>
    <td></td>
    <td>The time of the last edit of this record, in ISO8601
</td>
  </tr>

</table>


#### Description
An individual is a single organism (here typically a human).



#### Examples

```
{
   "biocharacteristics" : [
      {
         "description" : "Patient with Down syndrome",
         "type" : {
            "id" : "HP:0003745",
            "label" : "Genetic anticipation"
         }
      }
   ],
   "created" : "2017-10-25T07:06:03Z",
   "data_use_conditions" : {
      "id" : "DUO:0000004",
      "label" : "no restriction"
   },
   "description" : "patient with lung cancer, male smoker",
   "external_references" : [
      {
         "description" : "Cellosaurus cell line identifier",
         "relation" : "provenance",
         "type" : {
            "id" : "cellosaurus:CVCL_0312",
            "label" : "HOS"
         }
      }
   ],
   "geo_provenance" : {
      "altitude" : 94,
      "city" : "Timisoara",
      "country" : "Romania",
      "label" : "Str Marasesti 5, 300077 Timisoara, Romania",
      "latitude" : 45.75,
      "longitude" : 21.23
   },
   "id" : "AM_BS__NCBISKYCGH-1993",
   "info" : {
      "first_name" : {
         "type" : "string",
         "value" : "Ion"
      },
      "last_name" : {
         "type" : "string",
         "value" : "Tichy"
      }
   },
   "name" : "Ion Tichy, space explorer",
   "organism" : {
      "id" : "NCBITaxon:9606",
      "label" : "Homo sapiens"
   },
   "sex" : {
      "id" : "PATO:0020000",
      "label" : "female genetic sex"
   },
   "updated" : "2017-10-25T07:06:03Z"
}
```
--------------------------------------------------------------------------------

<h4>Notes and examples on the <i>Individual</i> properties</h4>

##### biocharacteristics

* list of Phenotype objects with properly prefixed term ids, describing features of the individual which are not specific to the reported biosample(s); typical examples here are sex, species and "systemic" phenotypes and diseases

* example:

```
'biocharacteristics' : [
  {
    'description' => 'Patient with Down syndrome',
    'type' => {
                'id' => 'HP:0003745',
                'label' => 'Genetic anticipation'
              }
  }
]
```

* Queries:  the query will return all individuals who have been properly labeled as human
```
db.individual.find( { "biocharacteristics.type.id" : "NCBITaxon:9606" } )
```
this call to the distinct funcion will return *all* HPO annotated classes
```
db.biosamples.distinct( { "biocharacteristics.type.id", "biocharacteristics.type.id" : { $regex : /HP\:/i } } )
```

##### created

* The creation time of this record, in ISO8601

* example:

```
'created' : "2017-10-25T07:06:03Z"
```

##### data_use_conditions

* Data use conditions applying to data from this individual, as ontology object (e.g. DUO).

* example:

```
'data_use_conditions' : {
  'id' => 'DUO:0000004',
  'label' => 'no restriction'
}
```

##### description

* A free text description of the individual.
* example:

```
'description' : "patient with lung cancer, male smoker"
```

##### external_references

* Different representations of the same record, not different records in relation with this individual

* example:

```
'external_references' : [
  {
    'description' => 'Cellosaurus cell line identifier',
    'relation' => 'provenance',
    'type' => {
                'id' => 'cellosaurus:CVCL_0312',
                'label' => 'HOS'
              }
  }
]
```

* Queries:  The query will return all individuals which have been reported in experiments in this publication.

```
db.individuals.find( { "external_references.type.id" : "pubmed:17440070" } )
```

##### geo_provenance

* This geo_class attribute ideally describes the geographic location of where this individual originates from.
This value may reflect either the place of birth or residence, but frequently may correspond to the place the study was performed.

* example:

```
'geo_provenance' : {
  'altitude' => 94,
  'city' => 'Timisoara',
  'country' => 'Romania',
  'label' => 'Str Marasesti 5, 300077 Timisoara, Romania',
  'latitude' => '45.75',
  'longitude' => '21.23'
}
```

##### id

* The local-unique identifier of this individual (referenced as "individual_id").
* example:

```
'id' : "AM_BS__NCBISKYCGH-1993"
```

##### info

* additional variant information, as defined in the example and accompanying documentation TODO this should be its own class
* example:

```
'info' : {
  'first_name' => {
                    'type' => 'string',
                    'value' => 'Ion'
                  },
  'last_name' => {
                   'type' => 'string',
                   'value' => 'Tichy'
                 }
}
```

##### name

* A short descriptive "name" for the individual, which may or may not correspond to a "real name". Unstructured text.

* example:

```
'name' : "Ion Tichy, space explorer"
```

##### organism

* An NCBI taxonomy term describing the species of the individual.
For resources where there may be more than one organism being studied it is advisable to indicate the taxonomic identifier of that organism, to it's most specific level

* example:

```
'organism' : {
  'id' => 'NCBITaxon:9606',
  'label' => 'Homo sapiens'
}
```

##### sex

* A PATO term describing the biological sex of the individual

* example:

```
'sex' : {
  'id' => 'PATO:0020000',
  'label' => 'female genetic sex'
}
```

##### updated

* The time of the last edit of this record, in ISO8601

* example:

```
'updated' : "2022-11-11T09:45:13Z"
```

