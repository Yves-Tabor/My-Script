# My-Script
Some exercices or katas I did

#A 6k by regexp

/*Complete the solution so that the function will break up camel casing, using a space between words.

Example
"camelCasing"  =>  "camel Casing"
"identifier"   =>  "identifier"
""             =>  "" */

function solution(str) {
    return str.replace(/([A-Z])/g, ' $1');
  }
