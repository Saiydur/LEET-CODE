# Intuition
The problem involves converting a Roman numeral string into an integer. To solve this problem, we can iterate through the input string and evaluate the corresponding integer value for each Roman numeral character. By considering specific cases such as subtraction (e.g., IV represents 4), we can calculate the final integer value.

# Approach
1. Initialize a variable total to store the accumulated integer value, starting from 0.
1. Iterate through the characters of the input string s using a for loop.
1. Use a switch statement to evaluate the value of each character and update total accordingly:
For the characters 'I', 'X', or 'C', check if the following character creates a subtraction case ('IV', 'IX', 'XL', 'XC', 'CD', 'CM'). If a subtraction case is found, add the corresponding value (4, 9, 40, 90, 400, 900) to total and increment i to skip the following character.
For the characters 'V', 'L', 'D', or 'M', add the corresponding value (5, 50, 500, 1000) to total.
1. For the character 'I', add the value 1 to total.
1. After iterating through all the characters, return the final value of total.
Complexity
# Time complexity: 
The algorithm iterates through each character in the input string once using the for loop. Therefore, the **time complexity is O(n)**, where n is the length of the string.
Space complexity: The algorithm uses a constant amount of extra space. Therefore, **the space complexity is O(1)**, which is constant.

# Code
```
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    let total = 0;
    for(let i = 0; i < s.length; i++) {
        switch(s[i]) {
            case 'I':
                if(s[i+1] === 'V') {
                    total += 4;
                    i++;
                } else if(s[i+1] === 'X') {
                    total += 9;
                    i++;
                } else {
                    total += 1;
                }
                break;
            case 'V':
                total += 5;
                break;
            case 'X':
                if(s[i+1] === 'L') {
                    total += 40;
                    i++;
                } else if(s[i+1] === 'C') {
                    total += 90;
                    i++;
                } else {
                    total += 10;
                }
                break;
            case 'L':
                total += 50;
                break;
            case 'C':
                if(s[i+1] === 'D') {
                    total += 400;
                    i++;
                } else if(s[i+1] === 'M') {
                    total += 900;
                    i++;
                } else {
                    total += 100;
                }
                break;
            case 'D':
                total += 500;
                break;
            case 'M':
                total += 1000;
                break;
        }
    }
    return total;
};
```