# My-Script
Some exercices or katas I did

#8 Kyu

There was a test in your class and you passed it. Congratulations!

But you're an ambitious person. You want to know if you're better than the average student in your class.

You receive an array with your peers' test scores. Now calculate the average and compare your score!

Return true if you're better, else false!

Note:
Your points are not included in the array of your class's points. Do not forget them when calculating the average score!

link: https://www.codewars.com/kata/5601409514fc93442500010b/train/javascript/68e2d9db9ab1fdbb127a8b58

solution : 
function betterThanAverage(classPoints, yourPoints) {
  const average = classPoints.reduce((sum, val) => sum + val, 0) / classPoints.length;
  return yourPoints > average;
}
____

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

_______

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement the function which takes an array containing the names of people that like an item. It must return the display text as shown in the examples:

[]                                -->  "no one likes this"
["Peter"]                         -->  "Peter likes this"
["Jacob", "Alex"]                 -->  "Jacob and Alex like this"
["Max", "John", "Mark"]           -->  "Max, John and Mark like this"
["Alex", "Jacob", "Mark", "Max"]  -->  "Alex, Jacob and 2 others like this"
Note: For 4 or more names, the number in "and 2 others" simply increases.

link: https://www.codewars.com/kata/5266876b8f4bf2da9b000362/train/javascript

Solution: 

function likes(names) {
  if(names.length === 0){
        return 'no one likes this';
    }else if(names.length === 1){
        return names[0]+' likes this';
    }
    else if(names.length === 2){
        return names[0]+" and "+names[1]+" like this";
    }else if(names.length === 3){
        return names[0]+", "+names[1]+" and "+names[2]+" like this";
    }else{
        const other = names.length - 2; 
        return names[0]+", "+names[1]+" and "+ other +" others like this";
    }
}
