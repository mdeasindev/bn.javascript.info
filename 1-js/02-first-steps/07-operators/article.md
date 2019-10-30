# অপারেটরস

আমরা স্কুল থেকেই অনেক অপারেটর সম্বন্ধে জানি। তারা ঠিক অনেকটা যোগ `+`, গুন `*`, বিয়োগ `-`, ইত্যাদির মত।

এই অধ্যায়ে, আমরা অপারেটরের দিকে মনোযোগ দিব যা স্কুলের গনিতেও অন্তর্ভুক্ত ছিলনা।

## টার্মসঃ "ঊনারি", "বাইনারি", "অপারেন্ড"

আমরা সামনে যাবার আগে, চলুন আমরা কিছু সাধারন পরিভাষা বুঝি।

- *একটি অপারেন্ড* -- হয় যা অপারেটরগুল দিয়ে প্রযুক্ত হয়। উদাহরণস্বরূপ, `5 * 2` এর গুনে, এখানে দুইটি অপারেন্ড আছেঃ বামের অপারেন্ডটি হল `5` এবং ডানের অপারেন্ডটি হল `2`. মাঝেমাঝে, লোকজন এইগুলোকে "অপারেন্ডস" এর পরিবর্তে "আরগুমেন্টস" বলে। 
- যদি একটি অপারেন্ড থাকে তাহলে সেটি হল একটি *ইউনারি* অপারেটর। উদাহরণস্বরূপ, এই ইউনারি নেগেশনটি `-` সংখ্যার মানটি উল্টিয়ে দেয়ঃ

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, unary negation was applied
    ```
- যদি দুইটি অপারেন্ডস থাকে তাহলে সেটি হল একটি *বাইনারি* অপারেটর। বাইনারিতেও মাইনাস প্রতীকটি একই থাকবেঃ

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binary minus subtracts values
    ```

    নিয়মানুসারে, উপরের উদাহরনে আমাদের দুইটি ভিন্ন অপারেটরস আছে যা একই প্রতীক ব্যবহার করেঃ নেগেশন অপারেটরটি হল একটি ইউনারি অপারেটর যা প্রতীকটিকেই উল্টিয়ে দেয়, এবং বিয়োগ অপারেটরটি হল একটি বাইনারি অপারেটর যা একটি সংখ্যা থেকে আরেকটি সংখ্যাকে বিয়োগ করে।

## স্ট্রিং সংযোগ, বাইনারি যোগ ( + )

এখন, চলুন দেখি জাভাস্ক্রিপ্ট এর বিশেষ বৈশিষ্ট্য যেটা স্কুলের গনিতেও ছিলনা।

সাধারণত, যোগ অপারেটর `+` সংখ্যাকে যোগ করে।

কিন্তু যদি বাইনারি `+` স্ট্রিং এর মদ্ধে ব্যবহার করা হয় তাহলে এটা এদেরকে যুক্ত করে দিবেঃ 

```js
let s = "my" + "string";
alert(s); // mystring
```

মনে রাখবেন যে, যদি অপারেন্ডগুলোর একটি যদি স্ট্রিং হয় তাহলে অপরটিকেও স্ট্রিং এ রূপান্তরিত করা হয়।

উদাহরণ স্বরূপঃ

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

দেখেন, প্রথম অপারেন্ড অথবা দ্বিতীয় অপারেন্ড স্ট্রিং কিনা এটা কোন ব্যাপার না। সহজ নিয়নঃ যদি যেকোনো একটি অপারেন্ড স্ট্রিং হয় তাহলে অপরটিও স্ট্রিং এ রূপান্তরিত হয়।

তবে, মনে রাখবেন যে অপারেশনগুলো চলে বাম থেকে ডান দিকে। যদি একটি স্ট্রিং এর আগে দুই এর অধিক সংখ্যা থাকে তাহলে স্ট্রিং এ রূপান্তরিত হওয়ার আগে সংখ্যাগুলোকে যোগ করা হবেঃ


```js run
alert(2 + 2 + '1' ); // "41" and not "221"
```

 স্ট্রিং সংযোগ এবং রূপান্তর হল বাইনারি প্লাস `+` এর একটি বিশেষ বৈশিষ্ট্যঃ অনন্যা গনিত অপারেটরগুলো শুধুমাত্র সংখ্যার সাথেই কাজ করে এবং সর্বদা তাদের অপারেন্ডগুলোকে সংখ্যায় রুপান্তর করে।

উদাহরণ স্বরূপঃ, বিয়োগ এবং ভাগঃ

```js run
alert( 2 - '1' ); // 1
alert( '6' / '2' ); // 3
```

## সংখ্যা রূপান্তর, ইউনারি +

যোগ `+` দুই ধরনের হয়ে থাকে: বাইনারি যেটা আমরা উপরে ব্যবহার করেছি এবং ইউনারি।

ইউনারি যোগ বা যোগ অপারেটরটি একক মানের উপর প্রযুক্ত হয়, এটা সংখ্যাকে কিছুই করে না কিন্তু অপারেন্ড যদি সংখ্যা না হয় তাহলে ইউনারি যোগ অপারেটরটি এটিকে সংখ্যায় রুপান্তরিত করে।

যেমনঃ

```js run
// No effect on numbers
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Converts non-numbers
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

এটা আসলে `Number(...)` ফাংশনের মত একই কাজ করে কিন্তু এটা সংক্ষিপ্ত।

সংখ্যায় স্ট্রিং রূপান্তর করার প্রয়োজনীয়তা অনেকবার দেখা যায়। যেমন,  যদি আমরা এইচটিএমএল এর ফর্ম থেকে যে মান পাই, সেগুলো সাধারনত স্ট্রিং হয়। কেমন হয় যদি আমরা এদেরকে যোগ করতে চাই?

বাইনারি যোগ হয়তো স্ট্রিং হিসেবে এদেরকে সংযুক্ত করে দিতঃ

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", the binary plus concatenates strings
```

যদি আমরা এদেরকে সংখ্যা হিসেবে ব্যবহার করতে চাই, আমাদেরকে সংখ্যায় রূপান্তর করতে হবে অ্যান্ড তারপর যোগ করতে হবেঃ

```js run
let apples = "2";
let oranges = "3";

*!*
// both values converted to numbers before the binary plus
alert( +apples + +oranges ); // 5
*/!*

// the longer variant
// alert( Number(apples) + Number(oranges) ); // 5
```

একজন গণিতবিদের দৃষ্টিকোণ থেকে, যোগের প্রাচুর্যতা কিছুটা অদ্ভুত বলে মনে হতে পারে। তবে একজন প্রোগ্রামারের দৃষ্টিকোণ থেকে, বিশেষ কিছু নেই: ইউনারি প্লাসগুলো প্রথমে চালিত হয়ে স্ট্রিংকে সংখ্যায় রূপান্তর করে এবং তারপর বাইনারি প্লাস এদেরকে যোগ করে দেয়।

কেন বাইনারির আগে ইউনারি প্লাসগুলো মানে চালিত হয়? আমরা দেখতে যাচ্ছি যে এটার কারন হল এদের *উচ্চতর প্রাধান্য*।

## Operator precedence

If an expression has more than one operator, the execution order is defined by their *precedence*, or, in other words, the default priority order of operators.

From school, we all know that the multiplication in the expression `1 + 2 * 2` should be calculated before the addition. That's exactly the precedence thing. The multiplication is said to have *a higher precedence* than the addition.

Parentheses override any precedence, so if we're not satisfied with the default order, we can use them to change it. For example, write `(1 + 2) * 2`.

There are many operators in JavaScript. Every operator has a corresponding precedence number. The one with the larger number executes first. If the precedence is the same, the execution order is from left to right.

Here's an extract from the [precedence table](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (you don't need to remember this, but note that unary operators are higher than corresponding binary ones):

| Precedence | Name | Sign |
|------------|------|------|
| ... | ... | ... |
| 16 | unary plus | `+` |
| 16 | unary negation | `-` |
| 14 | multiplication | `*` |
| 14 | division | `/` |
| 13 | addition | `+` |
| 13 | subtraction | `-` |
| ... | ... | ... |
| 3 | assignment | `=` |
| ... | ... | ... |

As we can see, the "unary plus" has a priority of `16` which is higher than the `13` of "addition" (binary plus). That's why, in the expression `"+apples + +oranges"`, unary pluses work before the addition.

## Assignment

Let's note that an assignment `=` is also an operator. It is listed in the precedence table with the very low priority of `3`.

That's why, when we assign a variable, like `x = 2 * 2 + 1`, the calculations are done first and then the `=` is evaluated, storing the result in `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

It is possible to chain assignments:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Chained assignments evaluate from right to left. First, the rightmost expression `2 + 2` is evaluated and then assigned to the variables on the left: `c`, `b` and `a`. At the end, all the variables share a single value.

````smart header="The assignment operator `\"=\"` returns a value"
An operator always returns a value. That's obvious for most of them like addition `+` or multiplication `*`. But the assignment operator follows this rule too.

The call `x = value` writes the `value` into `x` *and then returns it*.

Here's a demo that uses an assignment as part of a more complex expression:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

In the example above, the result of expression `(a = b + 1)` is the value which was assigned to `a` (that is `3`). It is then used for further evaluations.

Funny code, isn't it? We should understand how it works, because sometimes we see it in JavaScript libraries, but shouldn't write anything like that ourselves. Such tricks definitely don't make code clearer or readable.
````

## Remainder %

The remainder operator `%`, despite its appearance, is not related to percents.

The result of `a % b` is the remainder of the integer division of `a` by `b`.

For instance:

```js run
alert( 5 % 2 ); // 1 is a remainder of 5 divided by 2
alert( 8 % 3 ); // 2 is a remainder of 8 divided by 3
alert( 6 % 3 ); // 0 is a remainder of 6 divided by 3
```

## Exponentiation **

The exponentiation operator `**` is a recent addition to the language.

For a natural number `b`, the result of `a ** b` is `a` multiplied by itself `b` times.

For instance:

```js run
alert( 2 ** 2 ); // 4  (2 * 2)
alert( 2 ** 3 ); // 8  (2 * 2 * 2)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2)
```

The operator works for non-integer numbers as well.

For instance:

```js run
alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root, that's maths)
alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)
```

## Increment/decrement

<!-- Can't use -- in title, because built-in parse turns it into – -->

Increasing or decreasing a number by one is among the most common numerical operations.

So, there are special operators for it:

- **Increment** `++` increases a variable by 1:

    ```js run no-beautify
    let counter = 2;
    counter++;        // works the same as counter = counter + 1, but is shorter
    alert( counter ); // 3
    ```
- **Decrement** `--` decreases a variable by 1:

    ```js run no-beautify
    let counter = 2;
    counter--;        // works the same as counter = counter - 1, but is shorter
    alert( counter ); // 1
    ```

```warn
Increment/decrement can only be applied to variables. Trying to use it on a value like `5++` will give an error.
```

The operators `++` and `--` can be placed either before or after a variable.

- When the operator goes after the variable, it is in "postfix form": `counter++`.
- The "prefix form" is when the operator goes before the variable: `++counter`.

Both of these statements do the same thing: increase `counter` by `1`.

Is there any difference? Yes, but we can only see it if we use the returned value of `++/--`.

Let's clarify. As we know, all operators return a value. Increment/decrement is no exception. The prefix form returns the new value while the postfix form returns the old value (prior to increment/decrement).

To see the difference, here's an example:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

In the line `(*)`, the *prefix* form `++counter` increments `counter` and returns the new value, `2`. So, the `alert` shows `2`.

Now, let's use the postfix form:

```js run
let counter = 1;
let a = counter++; // (*) changed ++counter to counter++

alert(a); // *!*1*/!*
```

In the line `(*)`, the *postfix* form `counter++` also increments `counter` but returns the *old* value (prior to increment). So, the `alert` shows `1`.

To summarize:

- If the result of increment/decrement is not used, there is no difference in which form to use:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, the lines above did the same
    ```
- If we'd like to increase a value *and* immediately use the result of the operator, we need the prefix form:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- If we'd like to increment a value but use its previous value, we need the postfix form:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Increment/decrement among other operators"
The operators `++/--` can be used inside expressions as well. Their precedence is higher than most other arithmetical operations.

For instance:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Compare with:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, because counter++ returns the "old" value
```

Though technically okay, such notation usually makes code less readable. One line does multiple things -- not good.

While reading code, a fast "vertical" eye-scan can easily miss something like `counter++` and it won't be obvious that the variable increased.

We advise a style of "one line -- one action":

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitwise operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

These operators are used very rarely. To understand them, we need to delve into low-level number representation and it would not be optimal to do that right now, especially since we won't need them any time soon. If you're curious, you can read the [Bitwise Operators](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) article on MDN. It would be more practical to do that when a real need arises.

## Modify-in-place

We often need to apply an operator to a variable and store the new result in that same variable.

For example:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

This notation can be shortened using the operators `+=` and `*=`:

```js run
let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert( n ); // 14
```

Short "modify-and-assign" operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (right part evaluated first, same as n *= 8)
```

## Comma

The comma operator `,` is one of the rarest and most unusual operators. Sometimes, it's used to write shorter code, so we need to know it in order to understand what's going on.

The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated but only the result of the last one is returned.

For example:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (the result of 3 + 4)
```

Here, the first expression `1 + 2` is evaluated and its result is thrown away. Then, `3 + 4` is evaluated and returned as the result.

```smart header="Comma has a very low precedence"
Please note that the comma operator has very low precedence, lower than `=`, so parentheses are important in the example above.

Without them: `a = 1 + 2, 3 + 4` evaluates `+` first, summing the numbers into `a = 3, 7`, then the assignment operator `=` assigns `a = 3`, and the rest is ignored. It's like `(a = 1 + 2), 3 + 4`.
```

Why do we need an operator that throws away everything except the last expression?

Sometimes, people use it in more complex constructs to put several actions in one line.

For example:

```js
// three operations in one line
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Such tricks are used in many JavaScript frameworks. That's why we're mentioning them. But usually they don't improve code readability so we should think well before using them.
