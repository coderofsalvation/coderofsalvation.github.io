Flexible sql columns
====================

### Problem ###

When developing in never-ending iterations on a webproduct which is already in production, adding/laltering columns can have disastrous results.

### How to deal with it ###

Many things can be solved in many ways.
So, many people would suggest something like `better testing, better deployment strategies`.
However, I might have another interesting suggestion: `keep away from altering/adding columns`.

### Possible Solution: a yaml column ###

[YAML](http://en.wikipedia.org/wiki/YAML) is an awesome text markup which allows structures defined by text.

### Example ###

    ---
    receipt: Oz-Ware Purchase Invoice
    date: 2007-08-06
    customer:
        given: Dorothy
        family: Gale
            
So, why not add a 'yaml' column on certain tables which you expect to have more 'wild' columns?
You can even automate yaml-encoding/decoding upon often expected actions (Database CRUD operations).

### Benefits ###

  * its human readable
  * you can still search on it in Mysql using `LIKE "%family: Gale%"`
  * dynamic structures
  * you just deal with associative arrays

### Comfortable ###

The sutra PHP framework is a great example who exploits this feature: as soon as the databaselayer sees an 'yaml'-column, it automatically encodes/decodes it. 
The result is a very comfortable way of programming just with associative arrays, no need to worry about yaml-conversions.
            
