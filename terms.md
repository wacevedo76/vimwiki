# Programming Terms 
## 🔍 Declarative Programming – Defined
In declarative programming, you're telling the computer what the end result should be, and leaving it to the system or language runtime to figure out how to get there.

### 🆚 Declarative vs Imperative
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

### 🧪 In Practice: JavaScript Example
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

### 🧭 Why It Matters
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

### 🔧 Let's break that down:
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

## 🔄 Concurrency vs 🧵 Parallelism — Summary
| Concept    | Concurrency                                    | Parallelism                                     |
| ---------  | ---------------------------------------------- | ----------------------------------------------- |
| Definition | Managing multiple tasks at once                | Executing multiple tasks at the same time       |
| Key idea   | Structure — dealing with many things at once   | Speed — doing many things at once               |
| Focus      | Coordinating tasks (can be interleaved)        | Simultaneously executing tasks                  |
| Hardware   | Can happen on a single core (via interleaving) | Requires multiple cores/threads                 |
| Analogy    | A single cook juggling multiple dishes         | Multiple cooks each working on different dishes |

### 🔄 Concurrency – Defined
Concurrency is the ability of a system to handle multiple tasks seemingly at once by switching between them efficiently.
* It doesn’t necessarily mean tasks are running at the same instant.
* It's more about decomposition and scheduling.
* Often used in asynchronous programming, I/O handling, and event-driven systems.

### 🧠 Mindset:
"Let’s take turns."

#### Example (Single-core CPU):
```
Task A: ----->--->--->
Task B:   ----->--->--->
CPU switches between tasks rapidly (threading or async I/O)
```

### 🧵 Parallelism – Defined
Parallelism means performing multiple tasks at exactly the same time — typically on multiple processors or cores.
* It’s about using multiple computational units simultaneously.
* Useful for CPU-intensive computations (e.g., graphics, simulations, matrix operations).

### 🧠 Mindset:
"Let’s work at the same time."

#### Example (Multi-core CPU):
```
Core 1 runs Task A
Core 2 runs Task B
```
### 👷 Real-World Analogy
A Kitchen Analogy:
* Concurrency: A single chef preparing 3 dishes — he chops onions, then stirs a pot, then sets a timer. The tasks happen in overlapping time, but not literally at the same time.
* Parallelism: 3 chefs each make a different dish at the same time. True simultaneous execution.

### 🛠️ In Programming
Concurrency Tools:
* Threads
* Goroutines (Go)
* `async/await` (Python, JS)
* Event loops

Parallelism Tools:
* Multi-threading (on multi-core CPUs)
* GPU computing
* Parallel libraries (OpenMP, TBB, CUDA)

### ⚖️ How They Overlap and Differ
* Concurrency is a design pattern.
* Parallelism is an execution strategy.

A program can be:
* Concurrent but not parallel (e.g., async code on a single thread)
* Parallel but not concurrent (e.g., SIMD operations on data)
* Both (e.g., a web server with multiple threads handling I/O and parallel workers processing data)

###📌 Summary
| Feature            | Concurrency                    | Parallelism                                |
| ------------------ | ------------------------------ | ------------------------------------------ |
| Core focus         | Task coordination              | Task execution                             |
| Can run on 1 core? | ✅ Yes (via time-slicing)      | ❌ No (needs >1 core for true parallelism) |
| Language examples  | Java (threads), JS (async), Go | OpenMP, CUDA, multiprocessing libs         |
| Use case           | I/O-heavy apps, UIs, servers   | Heavy computation, simulations             |


