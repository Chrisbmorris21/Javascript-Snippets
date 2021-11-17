# Javascript-Snippets
Here is a repo of Javascript Snippets I have made which I can use in future for speed


## Getter to fetch largest ID in a mapped ID array from a larger array ##
```javascript

get nextAvailableID() {
    let biggest = 0;
    //get an array of the ids
    const recordIds = arrayData.map((record) => {
        if (record.id > biggest ) {
            biggest = record.id;
        }
        return record.id
    })
    return biggest+1;
}

```
