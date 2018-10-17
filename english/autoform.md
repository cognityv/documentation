# What is an autoform?

On the Cognityv Cloud Platform you are able to create diffenet views, forms and layout that you application needs, but sometimes it is just too much time to create a form from the basic components and you just need some user input programmatically, that is why we created the prompt functions and in them the autoform.

 # Autoform parameters

Properties with * means it is optional!

## String
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "string",
    "field": "field",
    "title": "Title",
    *"placeholder": ""
}
~~~~

## Number
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "number",
    "field": "field",
    "title": "Title",
    *"format": {
        "pattern": "0,0[.]00"
    }
}
~~~~

## Boolean
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "boolean",
    "field": "field",
    "title": "Title"
}
~~~~

## Slider
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "slider",
    "field": "field",
    "title": "Title",
    *"min": 0,
    *"max": 100
}
~~~~

## Color
Supported platforms: web ✔ mobile ︎✘

~~~~
{
    "type": "color",
    "field": "field",
    "title": "Title"
}
~~~~

## Enum
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "enum",
    "field": "field",
    "title": "Title"
    "values": ["one, "two", "three"]
}
~~~~

~~~~
{
    "type": "enum",
    "field": "field",
    "title": "Title",
    "values": [{ "label": "label1", "value": "value1"  }, { "label": "label2", "value": "value2" }]
    *"valueAttribute": "value",
    *"labelAttribute": "label",
    *"returnObject": true"
}
~~~~

## Selection
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "selection",
    "field": "field",
    "title": "Title"
    "values": ["one, "two", "three"]
}
~~~~

~~~~
{
    "type": "selection",
    "field": "field",
    "title": "Title",
    "values": [{ "label": "label1", "value": "value1"  }, { "label": "label2", "value": "value2" }]
    *"valueAttribute": "value",
    *"labelAttribute": "label",
    *"returnObject": true"
}
~~~~

## Date
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "date",
    "field": "field",
    "title": "Title",
    *"addTimezone": false,
    *"numeral": false,
    *"format": {
        *"locale": "en",
        "pattern": "YYYY-MM-DD:HH:mm"
    }
}
~~~~

## Barcode
Supported platforms: web ✘ mobile ✔

~~~~
{
    "type": "barcode",
    "field": "field",
    "title": "Title",
    *"multi": false
}
~~~~

## File
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "file",
    "field": "field",
    "title": "Title",
    *"publicfile": true,
    *"storage": "short-term" 
}
~~~~

**publicfile**: true means that everybody can have access to the file through an URL, false means you have to generate every time an access url that is only avaiable for 1-2 days.

**storage**: "short-term", "long-term", "shorttermtest-longtermprod"

Short term means the file will "disappear" in a day.
Long term means the file will stay forever or until it is intentionally dropped. 
Short term test - long term prod means, that in test environment it uses the short term storage in live/production environment it uses the long term storage. For testing purposes it can be ideal.


## Multi
Supported platforms: web ✔ mobile ✔

~~~~
{
    "type": "multi",
    "field": "field",
    "title": "Title",
    "params": [
      {
        "type": "string",
        "field": "field1",
        "title": "Title1"
      },
      {
        "type": "string",
        "field": "field2",
        "title": "Title2"
      }
    ]

}
~~~~

In the parameters you can input the parameters in an array like on the top level you would do.

 # Autoform general

General properties for every selector are:

~~~~
{
  "hide": true,
  "default": "",
  "icon": {
    "key": "add"
  },
  "clearable": false,
  "validation": [
    {
      "status": "error",
      "message": "Critical error!",
      "rules": [
        {
          "actualPath": "string",
          "operator": "_.isEqual",
          "expectedPath": "string2"
        }
      ]
    }
  ]
}
~~~~

**hide**: hide the selector

**default**: default value if none is given for the selector

**clearable**: makeing selected selector clearable or non clearable

**validation**: validate your result. if one rule ( [more about rules](./rules.md) ) fits your data then status is applied. statuses can be: "success", "warning", "error", "default"


 # Autoform special operators

These special operators can be applied on any of the selector parameters and they dynamically change the parameter.

## Router

~~~~
  "Router": [
    {
      "_rules": [
        {
          "path": "string",
          "rule": "_.isEqual",
          "assertTo": "hi"
        }
      ],
      "_value": true
    },
    {
      "_rules": [],
      "_value": false
    }
  ]
~~~~

## Switch

~~~~
  "Switch": {
    "default": [],
    "switchCasePath": "enum",
    "switchCaseKey": "brand",
    "switchValueKey": "models",
    "switchCases": []
  }
~~~~

## Ref

~~~~
  "Ref": "reference key"
~~~~

 # Autoform tabs and steps

The autoform parameters and selectors can be grouped together by steps or tabs by the following syntax. The layout in autoform options has to be set accordingly.

## Tabs

~~~~
{
  "icon": {
    "key": "clear"
  },
  "label": "main",
  "params": []
}
~~~~

In the parameters you can input the parameters in an array like on the top level you would do.

## Steps

~~~~
{
  "icon": {
    "key": "clear"
  },
  "label": "main",
  "params": []
}
~~~~

In the parameters you can input the parameters in an array like on the top level you would do.

 # Autoform options

 **Ref**: the references for the special operator

**clearable**: makeing all selectors clearable or non clearable

**layout**: "steps" | "tabs" | nothing

**type**: "edit" (default) | "view" | "editandview"

**savetitle**: title for save button

**nexttitle**: title for next button

**previoustitle**: title for previous button
