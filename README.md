## Finding gap in sequence array ##
**problem: Find the missing number in the array**
**e.g 1,2,3,_,5,6,7,9 Should return 4**
**If there is no gap in the sequence, return the next id that the record can occupy,**
**e.g. 1,2,3,4,5,6,7,8,9, Should return 10**


```javascript

//class declaration
    class data {
        constructor(arrayData){
            this.rawArray = arrayData;
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
