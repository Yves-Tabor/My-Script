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
____________

Your coworker was supposed to write a simple helper function to capitalize a string (that contains a single word) before they went on vacation.

Unfortunately, they have now left and the code they gave you doesn't work. Fix the helper function they wrote so that it works as intended (i.e. it must make the first character in the string upper case).

The string will always start with a letter and will never be empty.

Examples:

"hello" --> "Hello"
"Hello" --> "Hello" (the first letter was already capitalized)
"a"     --> "A"

Link:https://www.codewars.com/kata/595970246c9b8fa0a8000086/train/javascript/68c41cade322ebd4beae2c89
Solution: 
const capitalizeWord = word => {
  word.charCodeAt(0) < 96 ? return word;
  return word[0].toUpperCase()+word.slice(1);
}
_______________

Take an array and remove every second element from the array. Always keep the first element and start removing with the next element.

Example:
["Keep", "Remove", "Keep", "Remove", "Keep", ...] --> ["Keep", "Keep", "Keep", ...]

None of the arrays will be empty, so you don't have to worry about that!

Link: https://www.codewars.com/kata/5769b3802ae6f8e4890009d2/train/javascript/68c6a77e3571de5829234c52
Solution:
function removeEveryOther(arr){
  return arr.filter((_, index) => index % 2 === 0);
}

_______________

_______________________________________________________
_______________________________________________________


#7 Kyu

**

You are given an initial 2-value array (x). You will use this to calculate a score.

If both values in (x) are numbers, the score is the sum of the two. If only one is a number, the score is that number. If neither is a number, return 'Void!'.

Once you have your score, you must return an array of arrays. Each sub array will be the same as (x) and the number of sub arrays should be equal to the score.

For example:

if (x) == ['a', 3]  you should return [['a', 3], ['a', 3], ['a', 3]].

Link:https://www.codewars.com/kata/57eb936de1051801d500008a/train/javascript/68a08332e33ff646c5fdfa03
Solution: 
function explode(x) {
  let score = 0;

  
  if (typeof x[0] === 'number' && typeof x[1] === 'number') {
    score = x[0] + x[1];
  }
  else if (typeof x[0] === 'number') {
    score = x[0];
  }
  else if (typeof x[1] === 'number') {
    score = x[1];
  }
  else {
    return 'Void!';
  }

  return Array(score).fill(x);
}

______________

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

Examples
"This is an example!" ==> "sihT si na !elpmaxe"
"double  spaces"      ==> "elbuod  secaps"

Link: https://www.codewars.com/kata/5259b20d6021e9e14c0010d4/train/javascript/6889da347a5bbedb27d5fc4b
Solution:
let reverseWords = (str) => {
  return str
    .split(' ').map(word => word.split('').reverse().join(''))
    .join(' ');
};

_____________

Write a function that takes a single non-empty string of only lowercase and uppercase ascii letters (word) as its argument, and returns an ordered list containing the indices of all capital (uppercase) letters in the string.

Example (Input --> Output)
"CodEWaRs" --> [0,3,4,6]

Link: https://www.codewars.com/kata/539ee3b6757843632d00026b/train/javascript/68a36f32b02e9d523d76daa8
Solution: 
function capitals(word) {
  const result = [];
  for (let i = 0; i < word.length; i++) {
    if (word[i] === word[i].toUpperCase()) {
      result.push(i);
    }
  }
  return result;
}

________________

You are given a string of words and numbers. Extract the expression including:

the operator: either addition ("gains") or subtraction ("loses")
the two numbers that we are operating on
Return the result of the calculation.

Notes:

"loses" and "gains" are the only two words describing operators
No fruit debts nor bitten apples = The numbers are integers and no negatives
Examples
"Panda has 48 apples and loses 4"  -->  44
"Jerry has 34 apples and gains 6"  -->  40

link: https://www.codewars.com/kata/57b9fc5b8f5813384a000aa3/train/javascript/68e639c4173bb7a84f8d221c

solution: 
function calculate(string) {
  const ar = string.split(" ");
    const num = ar.filter((x)=> /\d/.test(x)).map((x)=> Number(x));
    if(ar.at(-2) === 'gains'){
        return num[0] + num[1];
    }else{
       return num[0] - num[1];
    }
}

______
You are going to be given a non-empty string. Your job is to return the middle character(s) of the string.

If the string's length is odd, return the middle character.
If the string's length is even, return the middle 2 characters.
Examples:
"test" --> "es"
"testing" --> "t"
"middle" --> "dd"
"A" --> "A"

link: https://www.codewars.com/kata/56747fd5cb988479af000028/train/javascript/68e3dafc2cbc1e7542640e69

solution: 

function getMiddle(s) {
  let index1 = ((s.length-1)/2);
  let index2 = s.length/2;
  
  if (s.length === 0){
    return '';
  }
  else if(s.length > 0 && s.length < 3){
    return s;
  }else{
     if(s.length%2 !== 0){
         return s.at(index1);
     }else{
            let first = s.slice(0,index2);
            let second = s.slice(index2);
            return first.at(-1)+second.at(0);
        }
     }
  }

______

Given a string, determine if it's a valid identifier.

Here is the syntax for valid identifiers:
Each identifier must have at least one character.
The first character must be picked from: alpha, underscore, or dollar sign. The first character cannot be a digit.
The rest of the characters (besides the first) can be from: alpha, digit, underscore, or dollar sign. In other words, it can be any valid identifier character.
Examples of valid identifiers:
i
wo_rd
b2h
Examples of invalid identifiers:
1i
wo rd
!b2h

link: https://www.codewars.com/kata/563a8656d52a79f06c00001f/train/javascript/68e53590a3a4e82702716bd9
solution: 
function isValid(str) {
   if (!str || str.length === 0) {
        return false;
    }
    const firstChar = str[0];
    if (!(/[a-zA-Z_$]/.test(firstChar))) {
        return false;
    }
    for (let i = 1; i < str.length; i++) {
        const ch = str[i];
        if (!(/[a-zA-Z0-9_$]/.test(ch))) {
            return false;
        }
    }
    return true;
}

___________

Example
input: "abcd", [0, 3, 1, 2]
output: "acdb"
Explanation
The character 'a' is placed at index 0.

The character 'b' is placed at index 3.

The character 'c' is placed at index 1.

The character 'd' is placed at index 2.

Notes
The string and the array will be of equal length.

The string will contain valid characters (A-Z, a-z, or 0-9);
the array will contain valid indices.

link: https://www.codewars.com/kata/5822d89270ca28c85c0000f3/train/javascript/68876139271018918f25facb
solution: 
function scramble(str, indices) {
  const result = Array(str.length);

  for (let i = 0; i < str.length; i++) {
    result[indices[i]] = str[i];
  }

  return result.join('');
}

___________________________________________________________
____________________________________________________________



#6 Kyu

______

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

Examples
[2, 4, 0, 100, 4, 11, 2602, 36] -->  11 (the only odd number)

[160, 3, 1719, 19, 11, 13, -21] --> 160 (the only even number)

Link: https://www.codewars.com/kata/5526fc09a1bbd946250002dc/train/javascript/68923001bf46fa6cb607aa6d
Solution:
const findOutlier = integers =>{
  if(integers.length<3) return 0;
  else{
    if(integers.filter((int)=> int%2 === 0).length >1) return Number(integers.filter((int)=> int%2 !== 0));
    return Number(integers.filter((int)=> int%2 === 0));
  }
}

______
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

______

Build up a method that takes a positive integer and formats it to a 'time - like' format.

The method must raise an exception if its hour length is less than 3 digits and greater than 4.

Examples:
800   --> '8:00'
1000  --> '10:00'
1451  --> '14:51'
3351  --> '33:51'
10000 --> raise an exception

link: https://www.codewars.com/kata/51e000d070fe4414000003f0/train/javascript/68e3dfefbcbf0866ce640eab

solution:

function solution(hour) {
    const h = String(hour);
  if(h.length>2 && h.length < 5){
      if (h.length === 3){
            return h.at(0)+":"+h.slice(1);
        }else{
            return h.slice(0,2)+":"+h.slice(2);
        }
  }
   else{
     throw new Error("raise an exception");   
    }
}
______

You wrote all your unit test names in camelCase. But some of your colleagues have troubles reading these long test names. So you make a compromise to switch to underscore separation.

To make these changes fast you wrote a class to translate a camelCase name into an underscore separated name.

Implement the ToUnderscore() method.

Example:

"ThisIsAUnitTest" => "This_Is_A_Unit_Test"

But of course there are always special cases...

You also have some calculation tests. Make sure the results don't get split by underscores. So only add an underscore in front of the first number.

Also Some people already used underscore names in their tests. You don't want to change them. But if they are not split correct you should adjust them.

Some of your colleagues mark their tests with a leading and trailing underscore. Don't remove this.

And of course you should handle empty strings to avoid unnecessary errors. Just return an empty string then.

Example:

"Calculate15Plus5Equals20" => "Calculate_15_Plus_5_Equals_20"

"This_Is_Already_Split_Correct" => "This_Is_Already_Split_Correct"

"ThisIs_Not_SplitCorrect" => "This_Is_Not_Split_Correct"

"_UnderscoreMarked_Test_Name_" => _Underscore_Marked_Test_Name_"

link: https://www.codewars.com/kata/5b1956a7803388baae00003a/train/javascript/68e7cd90069657cb5d368099

solution:
const toUnderScore = name => {
    const str = name.replace(/[A-Z]|\d+/g,char =>'_'+char);
    const ar = str.replace(/^_/, '').replaceAll("__",'_');
  return ar;
}
___________

Modify the kebabize function so that it converts a camel case string into a kebab case.

"camelsHaveThreeHumps"  -->  "camels-have-three-humps"
"camelsHave3Humps"  -->  "camels-have-humps"
"CAMEL"  -->  "c-a-m-e-l"
Notes:

the returned string should only contain lowercase letters

link:https://www.codewars.com/kata/57f8ff867a28db569e000c4a/train/javascript/68e7dab387aa1231733681bb
solution:
function kebabize(str) {
    return str.replace(/[A-Z]/g, char => "-"+char.toLowerCase()).replace(/\d+|^-/g, '');
}
__________

A string is considered to be in title case if each word in the string is either (a) capitalised (that is, only the first letter of the word is in upper case) or (b) considered to be an exception and put entirely into lower case unless it is the first word, which is always capitalised.

Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string -- it should behave in the same way even if the case of the minor word string is changed.

Arguments (Haskell)
First argument: space-delimited list of minor words that must always be lowercase except for the first word in the string.
Second argument: the original string to be converted.
Arguments (Other languages)
First argument (required): the original string to be converted.
Second argument (optional): space-delimited list of minor words that must always be lowercase except for the first word in the string. The JavaScript/CoffeeScript tests will pass undefined when this argument is unused.
Example
titleCase('a clash of KINGS', 'a an the of') // should return: 'A Clash of Kings'
titleCase('THE WIND IN THE WILLOWS', 'The In') // should return: 'The Wind in the Willows'
titleCase('the quick brown fox') // should return: 'The Quick Brown Fox'

Link: https://www.codewars.com/kata/5202ef17a402dd033c000009/train/javascript/68eac6c5e27b3e391b3925d3
Solution: 
const titleCase = (title, minorWords = "") => {
  if (!title) return ""; // handle empty string

  const minorSet = new Set(minorWords.toLowerCase().split(" "));
  return title
    .toLowerCase()
    .split(" ")
    .map((word, index) =>
      index === 0 || !minorSet.has(word)
        ? word[0].toUpperCase() + word.slice(1)
        : word
    )

____________

Complete the solution so that it returns true if it contains any duplicate argument values. Any number of arguments may be passed into the function.

The array values passed in will only be strings or numbers. The only valid return values are true and false.

Examples:

solution(1, 2, 3)             -->  false
solution(1, 2, 3, 2)          -->  true
solution('1', '2', '3', '2')  -->  true

Link: https://www.codewars.com/kata/520d9c27e9940532eb00018e/train/javascript/68ecc241e5b777e3c5589ae0
Solution: 
function solution(...args) {
  return new Set(args).size !== args.length;
}

____________

How can you remove duplication without Set method?

Solution: 
const remove = array =>{
    const result = [];
    for(let el of array){
        if(!result.includes(el)){
            const pusher = result.push(el);
        }
    }
    return result;
}

console.log(remove([2,4,4,5,5,6]));

__________________________________________________
__________________________________________________

#5 Kyu

______

In this kata, you will make a function that converts between camelCase, snake_case, and kebab-case.

You must write a function that changes to a given case. It must be able to handle all three case types:

js> changeCase("snakeCase", "snake")
"snake_case"
js> changeCase("some-lisp-name", "camel")
"someLispName"
js> changeCase("map_to_all", "kebab")
"map-to-all"
js> changeCase("doHTMLRequest", "kebab")
"do-h-t-m-l-request"
js> changeCase("invalid-inPut_bad", "kebab")
undefined
js> changeCase("valid-input", "huh???")
undefined
js> changeCase("", "camel")
""
Your function must deal with invalid input as shown, though it will only be passed strings. Furthermore, all valid identifiers will be lowercase except when necessary, in other words on word boundaries in camelCase.

(Any translations would be greatly appreciated!)

Link: https://www.codewars.com/kata/59be8c08bf10a49a240000b1/train/javascript/68e2d8cf165b2d7dc67a8a6f
Solution: 
function changeCase(input, targetCase) {
  if (typeof input !== 'string' || typeof targetCase !== 'string') return undefined;
  if (!['camel', 'snake', 'kebab'].includes(targetCase)) return undefined;
  if (input === '') return '';

  let words = [];

  if (/^[a-z]+(?:[A-Z][a-z]*)*$/.test(input)) {
    words = input.split(/(?=[A-Z])/).map(w => w.toLowerCase());
  } else if (/^[a-z]+(?:_[a-z]+)*$/.test(input)) {
    words = input.split('_');
  } else if (/^[a-z]+(?:-[a-z]+)*$/.test(input)) {
    words = input.split('-');
  } else {
    return undefined;
  }


  if (targetCase === 'camel') {
    return words[0] + words.slice(1).map(w => w[0].toUpperCase() + w.slice(1)).join('');
  }

  if (targetCase === 'snake') {
    return words.join('_'); 
  }

  if (targetCase === 'kebab') {
    return words.join('-');
  }

  return undefined;
}
____________

