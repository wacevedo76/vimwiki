# Programming Terms 
## 🔍 Declarative Programming – Defined
In declarative programming, you're telling the computer what the end result should be, and leaving it to the system or language runtime to figure out how to get there.

## 🆚 Declarative vs Imperative
To contrast this with imperative programming, here's a simple analogy:

| Task                | Imperative Approach                       | Declarative Approach          |
| ------------------  | ----------------------------------------- | ----------------------------- |
| Make a cup of tea   | Boil water → Put tea in cup → Pour water  | "I want a cup of tea"         |
| Filter even numbers | Use a loop, check if x % 2 == 0, store it | filter even numbers from list |
| Web UI with React   | Use declarative JSX like <Button />       | As opposed to DOM APIs in JS  |

## 🧠 Key Characteristics
* Focuses on the result, not the process.
* Code is often more concise and readable.
* You delegate control: the underlying system handles the flow.

## ✅ Examples of Declarative Paradigms
| Language/Technology | Declarative Element                            |
| SQL                 | SELECT name FROM users WHERE age > 30          |
| HTML                | <p>This is a paragraph</p>                     |
| CSS                 | color: red; font-size: 16px;                   |
| React               | Components & JSX define what UI looks like     |
| Haskell             | A pure functional, mostly declarative language |
| Prolog              | You declare facts and rules, not procedures    |

## 🧪 In Practice: JavaScript Example
* Imperative (how to double numbers):

```javascript
const nums = [1, 2, 3];
const doubled = [];
for (let i = 0; i < nums.length; i++) {
  doubled.push(nums[i] * 2);
}
```

* Declarative (what the result should be):
```javascript
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2);
```
In the declarative version, you say: "I want each number doubled"—not "loop through and double each number."

## 🧭 Why It Matters
Understanding declarative thinking helps you:
* Write cleaner, more maintainable code.
* Work with modern tools (like SQL, React, Terraform, Ansible, etc.)
* Shift toward higher-level abstraction and intent-focused programming.
* Would you like to see a breakdown of a specific declarative language or tool like SQL, HTML, or React?

```
You said:
So basically, the term Declarative simply means that the internal structure of whatever you want to do has been abstracted, making it simpler to do what you want to do?

ChatGPT said:
Yes — that's a very good summary.

To rephrase and expand on your point:

Declarative programming abstracts away the control flow and inner mechanics, so you can focus on what you want to achieve rather than how to achieve it.
```

## 🔧 Let's break that down:
* Imperative style = You manually control every step.
* Like giving step-by-step driving directions.

* Declarative style = You describe your goal, and the system figures out the steps.
* Like telling a GPS your destination.

### ✅ Examples in Your Words

| Task                     | Declarative Version (Your Summary)                                                 |
| Task                     | Declarative Version (Your Summary)                                                 |
| Styling a webpage        | Use CSS to say "make this red", rather than writing code that changes pixel colors |
| Querying data            | Use SQL to declare what you want: SELECT name FROM users                           |
| Creating UI              | Use React to declare how the UI should look in a state                             |
| Deploying infrastructure | Use Terraform to declare what infrastructure should exist, not how to provision it |

So yes: "Declarative" means the lower-level details are hidden or automated, and your job becomes expressing intent — the what, not the how.
* Culture
  - Culture is defined as "the attitudes and behavior of a particular social group"
