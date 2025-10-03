# My-Script
Some exercices or katas I did

#8 Kyu

#7 Kyu

#6 Kyu

_____
/*Complete the solution so that the function will break up camel casing, using a space between words.

Example
"camelCasing"  =>  "camel Casing"
"identifier"   =>  "identifier"
""             =>  "" */

function solution(str) {
    return str.replace(/([A-Z])/g, ' $1');
  }

_____

/*Given a positive integer n: 0 < n < 1e6, remove the last digit until you're left with a number that is a multiple of three.

Return n if the input is already a multiple of three, and if no such number exists, return null, a similar empty value, or -1.

Examples
1      => null
25     => null
36     => 36*/

const prevMultOfThree = n => {
    while(n>0){
    if(n%3===0) return n;
    n = Number(String(n).slice(0,-1));
    }
    return null;
}
1244   => 12
952406 => 9
