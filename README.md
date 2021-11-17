# Javascript-Snippets
Here is a repo of Javascript Snippets I have made which I can use in future for speed


## Getter to fetch largest ID in a mapped ID array from a larger array ##
```javascript

get nextAvailableID() {
    //set the biggest id to 0 by default
    let biggest = 0;
    //start a loop to map an array of only the ids
    const recordIds = arrayData.map((record) => {
        // if the record id being checked is larger than the currently set number
        // then change the number to the larger value
        if (record.id > biggest ) {
            biggest = record.id;
        }
        //map this records id to this array
        return record.id
        //loop
    })
    
    //increment the number so it doesn't replace the largest id
    return biggest+1;
}

```

This next code snippet declares a class which takes an array. It returns specific values from this array. 
In this case, I have only two getters, one gets the earliest available missing number in a sequence, the other gets the
next number available at the end of the sorted ID lists.

**problem: Find the missing number in the array
**e.g 1,2,3,_,5,6,7,9 Should return 4


```javascript
    class data {
        constructor(arrayData){
            this.rawArray = arrayData;
        }
        
        
        get idArray() {
            let idArray = [];
            arrayData.map((record) => {
                idArray.push(record.id);
            })
            return idArray;
        }
        
        get nextAvailableID() {
            let biggest = 0;
            
            const recordIds = arrayData.map((record) => {
                if (record.id > biggest ) {
                    biggest = record.id;
                }
                return record.id
            })
            return biggest+1;
        }
        get idGapInSequence(){
            let _freeVar = 0;
            for (let a = 0; a < arrayData.length; a++) {
                let b = a + 1;
                
                if (a != arrayData.length-1) {
                    
                    if (arrayData[b].id - arrayData[a].id > 1) {
                        let _freeVar = arrayData[a].id + 1
                        return _freeVar;
                    }
                }
            }
        }
        
        get storedData(){
            return this.rawArray;
        }
    }

    function nextCardID() {
        if (typeof dataObject.idGapInSequence == 'undefined') {
            return dataObject.nextAvailableID;
        } else {
            return dataObject.idGapInSequence;
        }
    }

    let dataObject = new data(arrayData);
    console.log(nextCardID());
    
```
