```

/*
Question #4: Checking for Uniqueness
Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

Example
Input: "heloh"

Output: false

Input: "copyright"

Output: true
*/

function checkUniqueness(inputString) {
    for (let i = 0; i < inputString.length; i++) {
        if (inputString.slice(i + 1).includes(inputString[i])){
            return false;
        } else {
            continue;
        }
    }
    return true;
}

console.log(checkUniqueness("copyrighti"));


/*
Question #3: Compressing Strings
Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

Example
Input: "aaabccdddda"

Output: "3ab2c4da"
*/

// /w recursion
function compressStringRecursively(inputString) {
    // base case
    if (inputString === "") {
    return "";
    }
    
    if (inputString[0] === inputString[1]) {
        let counter = 1;
        while (inputString[0] === inputString[counter]){
            counter++;
        }
        return counter + compressStringRecursively(inputString.slice(counter - 1));
    } else {
        return inputString[0] + compressStringRecursively(inputString.slice(1));
    }
}

console.log(compressStringRecursively("aaabccdddda"));


// w/o recursion
function compressString(stringInput) {
    let letter;
    let counter = 1;
    let output = "";
    
    for (let i = 0; i < stringInput.length; i++) {
        letter = stringInput[i] 
        if (stringInput[i] === stringInput[i + 1])
        {
            counter++;
        } else if (stringInput[i] !== stringInput[i + 1] && counter === 1) {
            output += letter;
        } else {
            output += counter + letter;
            counter = 1;
        }    
    }   
  
    return output;
}

console.log(compressString("aaabccdddda"));


/*
Question #2: Array Deduping
Write an algorithm that removes duplicates from an array. Do not use a function like filter() to solve this. Once you have solved the problem, demonstrate how it can be solved with filter(). Solve the problem with and without recursion.

Example
Input: [7, 9, "hi", 12, "hi", 7, 53]

Output: [7, 9, "hi", 12, 53]
*/

// /w recursion
function arrayDeduping(inputArray) {
    // base case
    if (inputArray.length === 0) {
        return inputArray;
    }
    
    const endElement = inputArray.pop();
    
    if (inputArray.includes(endElement)) {
        return arrayDeduping(inputArray);    
    } else {
        return arrayDeduping(inputArray).concat([endElement]);
    }
}

console.log(arrayDeduping([7, 9, "hi", 12, "hi", 7, 53]));

// w/o recursion
function removeDupes(inputArray) {
    let noDupes = [];
    const sort = [...inputArray]
    sort.sort();
    
    inputArray.forEach(e => {
        if (sort[sort.indexOf(e)] == sort[sort.indexOf(e) + 1]) {
            inputArray.splice(inputArray.lastIndexOf(e), 1)                // if index of "hi" and index of "hi" + 1 equal, they are dupes, thus remove 1 "hi" with splice inputArray.indexOf("hi")
        } 
    });
    
    return inputArray;
}

console.log(removeDupes([7, 9, "hi", 12, "hi", 7, 53]));

// /w filter()
// the filter method filters through an array, returning an array of only passing conditions given for each element checked
function filterOutDupes(inputArray) {
    return inputArray.filter( (e, i, arr) => { 
        if (inputArray.lastIndexOf(e) !== i) {
            arr.splice(inputArray.lastIndexOf(e), 1);
        }
        return e
    });
}

console.log(filterOutDupes([7, 9, "hi", 12, "hi", 7, 53]));


/*
Question #1: Turning Strings to URLs
URLs cannot have spaces. Instead, all spaces in a string are replaced with %20. Write an algorithm that replaces all spaces in a string with %20.

You may not use the replace() method or regular expressions to solve this problem. Solve the problem with and without recursion.

Example
Input: "Jasmine Ann Jones"

Output: "Jasmine%20Ann%20Jones"
*/
                 
// /w recursion
function replaceStringRecursively(inputString) {
    //base case & termination case
    if (inputString == "" || !isNaN(inputString)) {
    return "";
    }
    //console.log(inputString.slice(0, inputString.length - 1));
    
    if (inputString[inputString.length - 1] === " ") {
        return replaceStringRecursively(inputString.slice(0, inputString.length - 1)) + "%20";
    } else {
        return replaceStringRecursively(inputString.slice(0, inputString.length - 1)) + inputString[inputString.length - 1]
    }
}

console.log(replaceStringRecursively("Jasmine Ann Jones"));
                                                                                             


// w/o recursion and /w currying and closure
const replaceString = (replace) => {
    return (replacement) => {
        return (stringInput) => {
            return stringInput.split(replace).join(replacement);
        }
    }
}

const urlSpaceEncoder = replaceString(" ")("%20");

console.log(urlSpaceEncoder("Jasmine Ann Jones"));

```
