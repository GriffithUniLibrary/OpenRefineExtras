---
title: Dates
nav: true
---

### How to change various date formats

You can parse a column containing dates in different formats, such as cells with `Nov-09` and `11/09`, using GREL:

`value.toDate('MM/yy','MMM-yy').toString('yyyy-MM')`

and both will output `2009-11`. 

For example, the GREL expression:

`value.toDate('yyyy-MM-dd','EEE MMM dd Z yyyy').toString('yyyy-MM-dd')`
    
- `'yyyy-MM-dd'` is for example `2020-10-09` 
- `'EEE MMM dd Z yyyy'` for example `Wed Dec 09 +0000` (which is the time zone) `2020`

You need to assess each of the different date formats and add those to the first part of the argument.

Then tell OpenRefine what you would like all the variations changed to in the second brackets. 
- such as `'yyyy-MM-dd'` or `'yy-MM-dd'` or `'dd-MM-yyyy'` etc. 

The functions are explained here [https://docs.openrefine.org/manual/grelfunctions/#date-functions](https://docs.openrefine.org/manual/grelfunctions/#date-functions).
