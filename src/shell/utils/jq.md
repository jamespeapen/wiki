# jq

`jq` is a JSON parser.

All examples are run on this object which will be referred to as `json`.

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [],
  "spouse": null
}
```

## Extract a top-level field

```bash
# firstName
jq '.firstName' json

## "John"
```

```bash
# age
jq '.age' json

## 27
```

## Extracting lower level fields

#### Get all fields of the `address` object

```bash
jq '.address' json

## {
##   "streetAddress": "21 2nd Street",
##   "city": "New York",
##   "state": "NY",
##   "postalCode": "10021-3100"
## }
```

##### [] for output without object keys

```bash
jq '.address[]' json -r # raw output wihout quotes

## 21 2nd Street
## New York
## NY
## 10021-3100
```

#### Single key

```bash
jq '.address.streetAddress' json

## "21 2nd Street"
```

## Extract multiple fields

```bash
jq '.firstName,.lastName' json

## "John"
## "Smith"
```

The default behaviour is to print each filed on a new line. To get them on the
same line, use `+` to concatenate the fields. This operator can be used to
add other strings like spaces and punctuation.

```bash
jq '.firstName + .lastName' json

## "JohnSmith"

jq '.firstName + " " + .lastName' json

## "John Smith"

jq '.lastName+ ", " + .firstName ' json

## "Smith, John "
```

### Extract multiple fields hierarchically

To get multiple fields under the same object, use `.object | .key` to get the
values.

```bash
jq -r '.address | .city + ", " + .state' json

## New York, NY
```

### Lists

Lists can be indexed during retrieval. Objects cannot be indexed with numbers.

#### Empty [] retrieves all elements

```bash
jq -r '.phoneNumbers[]' json

## {
##   "type": "home",
##   "number": "212 555-1234"
## }
## {
##   "type": "office",
##   "number": "646 555-4567"
## }
```

#### Indexing

```bash
jq '.phoneNumbers[0].type' json

## "home"

jq '.phoneNumbers[0,1].type' json

## "home"
## "office"
```

#### Retrieve all elements of a list

```bash
jq '.phoneNumbers[] | .type' json

## "home"
## "office"
```

#### All elements with formatting

```bash
jq -r '.phoneNumbers[] | .type + ": " + .number' json

## home: 212 555-1234
## office: 646 555-4567
```
