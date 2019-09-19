---
title: 'Info'
layout: default
permalink: "/schemas/blocks/Info.html"
excerpt_separator: <!--more-->
category:
  - schemas
tags:
  - code
---
## Info


#### Status: __proposed__

<!--more-->



#### Provenance


#### Authors

*

#### Schema source: [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/working/info.yaml)
#### Properties of the _Info_ class

<table>
  <tr>
    <th>Property</th>
    <th>Type</th>
    <th>Format</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td></td>
    <td>an optional free-text annotation about the object</td>
  </tr>
  <tr>
    <td>format</td>
    <td>string</td>
    <td></td>
    <td>format of the value; optional</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td></td>
    <td>type of the value; optional</td>
  </tr>
  <tr>
    <td>value</td>
    <td></td>
    <td></td>
    <td>the value in a format correstponding to type</td>
  </tr>

</table>


#### Description
Additional information regarding the object in reference.



#### Examples

```
{
   "description" : "The base length of the called segment",
   "format" : "int64",
   "type" : "number",
   "value" : 1503320
}
```
--------------------------------------------------------------------------------

<h4>Notes and examples on the <i>Info</i> properties</h4>

##### description

* an optional free-text annotation about the object
* example:

```
'description' : "The base length of the called segment."
```

##### format

* format of the value; optional
* example:

```
'format' : "int64"
```

##### type

* type of the value; optional
* example:

```
'type' : "number"
```

##### value

* the value in a format correstponding to type
* example:

```
'value' : "1503320"
```

