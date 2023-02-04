```

/* 
Compress strings
take input of string with repeated characters
output string compressed using a number to show many times the repeated character was compressed
"aaa" === "3a"
"ab" === "ab"

input: "aaabccdddda"
output: "3ab2c4da"
*/ 

// w/o recursion
function compressString(stringInput) {
    let letter;
    let counter = 1;
    let output = "";
    
    for (let i = 0; i < stringInput.length; i++) {                                // loop through the string, for each letter, check if the letter of letter index + 1 === letter
        letter = stringInput[i]        // a    
        if (stringInput[i] === stringInput[i + 1]) {        // a === a                               
            counter++                                   // IF true, counter++
        } else if (stringInput[i] !== stringInput[i + 1] && counter === 1 ) {
            output += letter;
        } else {
            output += counter + letter                                // IF false, add letter at index to output
            counter = 1;
        }
    }
    
    return output;
}

console.log(compressString("aaabccdddda"));

// recursive

// if (stringInput[i] === stringInput[i + 1])
// counter = 1;
// while (stringInput[i] === stringInput[i + counter] {
//       counter++;
//}
// return counter + stringInput[i] + recursiveFun(string(lessend)

```