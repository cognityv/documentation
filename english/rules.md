# What are rules for?

With rules you can apply different assertations for the data currently used.

# Operators

* _.isEqual
* _.isArray
* _.isBoolean
* _.isDate
* _.isEmpty
* _.isInteger
* _.isNaN
* _.isNull
* _.isNumber
* _.isObject
* _.isPlainObject
* _.isRegExp
* _.isString
* _.isUndefined
* greaterThan
* lessThan
* greaterOrEqual
* lessOrEqual
* includes
* lengthIsOver
* lengthIsEqual
* lengthIsLess
* validEmail

 # Rule description

**simple**

~~~~
{
  "actualPath": "path",
  "operator": "_.isEqual",
  "expectedValue": "string"
}
~~~~

This simple rule discribes an "_.isEqual" assertation between the value on the path "string" and the value "string".

Both "actualValue" and "expectedValue" can be set as a fix value and both "actualPath" and "expectedPath" can be set as a dynamic value. The paths can be set as a string or as an object where you can add additional parameters like "global": true where the path string is applied to the global state and not the local state (can be useful inside a multiply/multi).

~~~~
{
  "actualPath": {
    "path": "string",
    "global": true
  }
}
~~~~
