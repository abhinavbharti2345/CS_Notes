
## <font color="#ffc000">1. Variables</font>

You already know this, but quick refresh:

```
const name = "Abhinav";
let age = 20;
```

- `const` → value/reference shouldn't be reassigned
- `let` → can be reassigned

---

## <font color="#ffc000">2. Functions</font>

A function is a reusable block of code.

```
function add(a, b) {
    return a + b;
}

const result = add(2, 3);

console.log(result); // 5
```

### Important: parameters vs arguments

```
function greet(name) {   // name = parameter
    return "Hello " + name;
}

greet("Abhinav");        // "Abhinav" = argument
```
---

## <font color="#ffc000">3. Arrow Functions</font>

- Arrow functions are a **shorter syntax for writing functions**.
- Syntax:

```
const functionName = (parameters) => {
    // code
};
```

### Examples

**Normal function:**

```
function add(a, b) {
    return a + b;
}
```

**Arrow function:**

```
const add = (a, b) => {
    return a + b;
};
```

### Short form

If the function has only **one expression to return**, `{}` and `return` can be removed:

```
const add = (a, b) => a + b;
```

```
const square = x => x * x;
```

### Parameters

**No parameters:**

```
const hello = () => {
    console.log("Hello");
};
```

**One parameter:**

```
const square = x => x * x;
```

Parentheses around one parameter are optional:

```
const square = (x) => x * x;
```

**Multiple parameters:**

```
const multiply = (a, b) => a * b;
```

### Arrow Functions as Values

Functions can be stored in variables:

```
const greet = () => {
    return "Hello";
};

console.log(greet());
```

They can also be passed to other functions, which is why arrow functions are commonly used as **callbacks**:

```
numbers.map(x => x * 2);
```

### Important

- Arrow functions are **not mandatory**. Normal functions work too.
- Main advantage: **shorter and cleaner syntax**, especially for small functions/callbacks.
- Arrow functions have different `this` behavior from normal functions. This is an advanced topic to learn later.
---

# <font color="#ffc000">4. Objects</font>

An object stores related data as **key-value pairs**.

```
const user = {
    name: "Abhinav",
    age: 20
};
```

Access values:

```
user.name
user.age
```

Output:

```
Abhinav
20
```

Your routes are objects:

```
const route = {
    method: "GET",
    path: "/users",
    handler: () => "Users"
};
```

So:

```
route.method
```

→ `"GET"`

```
route.path
```

→ `"/users"`

```
route.handler()
```

→ `"Users"`

### Nested objects

You'll also return:

```
return {
    statusCode: 404,
    body: {
        error: "Not Found"
    }
};
```

That's an object containing another object.

---

# <font color="#ffc000">5. Arrays</font>

An array stores multiple values:

```
const numbers = [10, 20, 30];
```

You can access them:

```
numbers[0] // 10
numbers[1] // 20
```

Your `routes` is an array of objects:

```
const routes = [
    {
        method: "GET",
        path: "/users",
        handler: () => "Users"
    },
    {
        method: "POST",
        path: "/users",
        handler: () => "Created"
    }
];
```

Think of it as:

```
routes
 │
 ├── route 0
 │    ├── method
 │    ├── path
 │    └── handler
 │
 └── route 1
      ├── method
      ├── path
      └── handler
```

---

# <font color="#ffc000">6. `for...of` Loop </font>🔄

Suppose you have an array:

```
const fruits = ["apple", "banana", "mango"];
```

You can loop through it:

```
for (const fruit of fruits) {
    console.log(fruit);
}
```

Output:

```
apple
banana
mango
```

Think:

> **For every `fruit` inside `fruits`, do this.**

### Numbers

```
const numbers = [10, 20, 30, 40];

for (const number of numbers) {
    console.log(number * 2);
}
```

Output:

```
20
40
60
80
```

### Why `for...of`?

It's simply a clean way to get **each value** from an array.

---

<font color="#ffc000"># 7. `if / else` Conditions</font>

Conditions let your program make decisions.

```
const age = 20;

if (age >= 18) {
    console.log("You can vote");
} else {
    console.log("You cannot vote");
}
```

Since `20 >= 18` is true:

```
You can vote
```

### Multiple conditions

You can use `else if`:

```
const marks = 75;

if (marks >= 90) {
    console.log("A");
} else if (marks >= 70) {
    console.log("B");
} else if (marks >= 50) {
    console.log("C");
} else {
    console.log("Fail");
}
```

Output:

```
B
```

---

# <font color="#ffc000">8. `.toLowerCase()`</font> 🔤

This converts a string to lowercase.

```
const name = "ABHINAV";

console.log(name.toLowerCase());
```

Output:

```
abhinav
```

Another example:

```
const answer = "YES";

if (answer.toLowerCase() === "yes") {
    console.log("User said yes");
}
```

This works even if the user enters:

```
YES
Yes
yEs
yes
```

because all of them become:

```
yes
```

## <font color="#ffc000">9. `.split()` — String Method</font>

- `.split(separator)` **splits a string into an array** using the given separator.

```
const text = "apple,banana,mango";

const fruits = text.split(",");

console.log(fruits);
// ["apple", "banana", "mango"]
```

- The separator can be any string:

```
const date = "13-08-2026";

const parts = date.split("-");

console.log(parts);
// ["13", "08", "2026"]
```

- Access individual elements normally:

```
parts[0]; // "13"
parts[1]; // "08"
parts[2]; // "2026"
```

**Remember:** `string → split() → array`

---

## <font color="#ffc000">10. Functions as Values</font>

- In JavaScript, **functions can be stored in variables**.

```
const sayHello = function() {
    console.log("Hello");
};
```

- Arrow functions can also be stored in variables:

```
const sayHello = () => {
    console.log("Hello");
};
```

- Call the function using `()`:

```
sayHello();
```

### Functions can be passed to other functions

```
function execute(action) {
    action();
}

const sayHello = () => {
    console.log("Hello");
};

execute(sayHello);
```

Here:

```
execute(sayHello);
```

passes the **function itself**.

```
action();
```

calls that function.

**Remember:** In JS, functions are **values** → they can be stored, passed, and returned.