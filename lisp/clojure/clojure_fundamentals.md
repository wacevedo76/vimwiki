# Clojure Fundamentals
```  
  Clojure documentation      | (doc <name of function or macro>)
```

##  Core data structures 
```
  NOTE: Commas are not       |
  evaluated in expressions   |   nil
  (evaluated as whitespace)  |   true false                       :boolean
  so they are not needed but |   \a \b \b, etc...                 :Characters
  can be used as visual      |   "foo"                            :string
  separators (maps)          |   ; end of line comment
                             |   ;; full line comment
                             |   ;;; block comment
                             |   foo, 'foo                        :symbol
                             |   :foo                             :keyword
                             |
                             | Collections
                             |
                             |   '(1 2 3 4 5) / (list 1 2 3 4 5)  ; List
                             |   ["a" "b" "c" "d" "e"]            ; Vector
                             |   {:name "Grogu", :age 50}         ; Map
                             |   #(5 2 3 1 4)                     ; Set
```
##  Function calls 
```
                             |   (function arg-1 arg-2 ...)
                             |   (max 1 2 3)                      ; => 6
                             |   (filter odd? [1 2 3])            ; => (1 3)
                             |
(conditional)                |   (if (< 1 2) "a" "b")             ; => "a"
                             |
Immutability                 | All data structures in Clojure are immutable
                             |
Define variables             | (def first-name "Dave")
                             | (def ages [42 3 18])
                             |
  string concatinaion        | (str "I'm sorry " first-name)    ; => "I'm sorry Dave"
  conjoin (append) value     | (conj ages 21)                   ; => [42 3 18 21] (ages doesn't change)
                             |
                             |
Syntactic sugar for function | (defn greetings [name]             ; uses defn (define function)
Declarations                 |   (str "Hello" name))
                             |
Functions calls are the same | (greetings "Dave")                 ; => "Hello Dave"
                             |
Nested functions             | (filter odd? (map inc (range 5)))  ; => (1 3 5)
                             |
"Thread Last" for structuing | (->> (range 5)                     ; => (0 1 2 3 4)
Nested function to be more   |      (map inc)                     ; => (1 2 3 4 5)
natural (to read)            |      (filter odd?))                ; => (1 3 5)
                             |
                             | (->> Acts as sort of a pipe (Unix pipe)
```
## Collections
```
  List                       | '(1 2 "tom") <- start with a quote, separating commas are optional
                             |   - Elements are accessed sequentially
                             |
      Return 1st element     | (def testlist '(1 2 3 4 5))
                             | (peek testlist)  ;=> 1
                             |
      Return all but first   | (pop testlist)  ;=> (2 3 4 5)
      element of list        |
                             |
      Count                  | (count (list 1 2 3 4 5))  ;
                             |
                             |
  Vector                     | [:test01 2 3 4 5 :test2]
                             |   - Elements are accessed by index
                             |     (def family ["bob" "jim" "Sally"])
                             |     (family 1)           ;; output: "jim"
                             |
      Modify a vector        | (def the-vector [10 20 30 40 50])
                             | ;; (assoc (list) (list index) (new value))
                             | (assoc the-vector 2 25)  -> [10 20 25 40 50]
                             |
      Retrieve a value from  | (get the-vector 2)  ;=> 30  -> returns nil if value isn't found
      a vector               | (nth the-vector 2)  ;=> 30  -> throws an error if value isn't found
                             |
      return vector element  | (the-vector 3)  ;=> 40
      using an index         |
                             |
      Add a value to vector  | (conj [1 2 3 4 5] 6)  ;=> [1 2 3 4 5 6]
                             | ;; appends the new value to the end
```
## Lists and Vectors
```
  Access first element       | (first '(:rabbit :pocket-watch :marmalade :dorr))
                             | ;; -> :rabit
                             |
  Access all but first       | (rest '(:rabbit :pocket-watch :marmalade :dorr))
  element                    | ;; -> :pocket-watch :marmalade :door
                             |
  Access the last element    | (last '(:rabbit :pocket-watch :marmalade :door))
                             | ;; -> :door
                             |
  Access the nth element     | (nth [:rabbit :pocket-watch :marmalade :door] 2)
  (faster with vectors)      | ;; -> :marmalade ()
                             |
  Add element an to the start| (cons 2 '(3 4))
  of a collection            | ;; -> (2 3 4)
                             |
  Add elemnt to the end      | (conj [:first :second] :third])
  of a vector                |
                             |
  count the number of elemen-| (conj [:toast :butter] :jam)
  ts in a colletion          | ;; -> [:toast :butter :jam]
                             |
  (conj adds elements to the | (conj [:toast :butter] :jam :honey)
  end of vectors, it adds to | ;; -> [:toast :butter :jam :honey]
  the begining of list       |
```

## Maps
```
  Basic Strucute             | {:jam1 "strawberry" :jam2 "blackberry"}
    ;; commas are optional   | ;; - {:jam2 "blackberry" :jam1 "strawberry"}
                             |
    Alternate assignment     | (hash-map :a 1 :b 2 :c 3)
                             |
                             |
  Retrieve (get) the value   | (get {:jam1 "Strawberry" :jam2 "blackberry"} :jam2) / (:jam2 {:jam1 "Strawberry" :jam2 "blackberry"})
  from a item in a map       | ;; -> "blackberry"
                             |
                             | (def the-map {:a 1 :b 2 :c 3})
                             |
                             | (the-map :b)  ;=> 2
                             |
                             | (:b the-map)  ;=> 2
                             |
     Set default value       | (:d the-map 26)  ;=> 26
                             |
  inserting a new key / val  | (assoc hash_map :d 4 )
                             |
  removing a key / val       | (dissoc hash_map a:)
                             |
                             |
  set a default value if     | (get {:jam1 "strawberry" :jam2 "blackberry"} :jam3 "not found")
  a key in map is not present| ;; -> "not found"
                             |
  get using the key as a     | {:jam2 {:jam1 "strawberry" :jam2 "blackberry" :jam3 "marmalade"}}
  function                   | ;; -> "blackberry"
                             |
  Return only the keys of    | (keys {:jam1 "strawberry" :jam2 "blackberry" :jam3 "marmalade"})
  a map                      | ;; -> {"marmalade" "blackberry" "stawberry"}
                             |
  Update value in nested map | (assoc-in map [key & more-keys] value)  -> Changes value
                             |
                             | (update-in map [key & more-keys] update-function & args)
```
## Sets                         
```
                             | Sets are very useful for when you have a
                             | collection of elements with no duplicates. You
                             | can recognize them by the surrounding #{}
                             |
                             | #{:red :blue :white :pink} ;;-> #{:red :blue :white :pink}
                             |
                             | ;; No duplicates allowed in the set at creation
                             | #{:red :blue :white :pink :pink} ;;-> illegalArgumentException Duplicate key: :pink
                             |
  union                      | The *union* function takes the combined items of
                             | all of the sets:
                             |
                             | (clojure.set/union #{:r :b :w} #{:w :p :y})
                             |   ;; -> #{:y :r :w :b :p}
                             |
  difference                 | The *difference* function is almost like subtraction.
                             | It takes the elements away from on of the sets:
                             |
                             | (clojure.set/difference #{:r :b :w} #{:w :p :y})
                             |   ;; -> #{:r :b}
                             |
  intersection               | The *intersection* function returns only the
                             | shared elements between sets:
                             |
                             | (clojure.set/intersection #{:r :b :w} #{:w :p :y})
                             |   ;; -> #{:w}
                             |
  Converting to sets         | You can convert another type of collection to set
                             | using the *set* function. This is useful for using set
                             | operations on things like vectors. Maps can be
                             | converted t osets as well. The key-value pairs are
                             | turned into vectors
                             |
                             | (set [:rabbit :rabbit :watch :door])
                             |   ;; - > #{:door :watch :rabbit}
                             |
                             | (set {:a 1 :b 2 :c 3})
                             |   ;; -> #{[:c 3] [:b 2] [:a 1]}
```
  
## Define variable
```
                             | (def x 42) -> use the def keyword, variable name
                             |              then value
                             |
  Define new function        | (def greetings (fn [name] (str "Hello " name)))   <- is this how lamda functions are made?
  (using def)                |    -> use the "def" keyworkd then function name
                             |       parameters listed between brackets "[]"
                             |       then the body of the function within "()"
                             |       if you use the "def" keyword then you must
                             |       use "fn" keyworkd as the first items in the
                             |       body of the function
                             |
  Define a function
  (using defn)               | (defn foo [x] (* x 2))
                             |
  Define anonymous functions | (fn [x y] (+ x y))
                             |
  Call a function with items | (apply + [1 2]) == (+ 1 2)
  of a sequence as individual|
  arguments                  |
                             | 
  Define local variables     | (let [a 5]               ;; a = 5
                             |    (println "a = " a)
                             |    (inc a))
                             |
  Multiple variables         | (let [a 5
                             |       b 7]
                             |    (println "a =" a)
                             |    (println "b =" b)
                             |    (+ a b))
```

### Built in Math operations
```
  Modulo                     | (mod 23 2)
                             | ;; -> 1
                             |
  Max (returns the max num   | (max 1 2 3 99 5 7)
    from list)               | ;; -> 99
                             |
  Min                        | (min 3 4 5 99 3)
                             | ;; -> 3
                             |
  Random (rational number)   | (rand 100)
                             | ;; -> 37.51551833853015 (for example)
                             |
  Random Integer             | (rand-int 100)
                             |
  PI                         | (Math/PI)
  (The Math module contains  |
   many mathimatical operat- |
   ions                      |
``` 
## Characters and Strings
```
  Single Character           | \H, \w
                             |
  String                     | "Hello", "World!"
                             |
  Regular Expressions        | #"[0-9]+"
                             |
  Get the length of string   | (.length "Hello!")
                             | ;; -> 6
                             |
  Convert to lower case      | (.toLowerCase "Hello!")
                             | ;; -> "hello!"
                             |
  Convert to upper case      | (.toUpperCase "Hello!")
                             | ;; -> "HELLO!"
                             |
  Return a character from a  | (.charAt "Hello!" 3)
  specific position          | ;; -> \l
```

## Control Structures
```
  if                         | (if test consequent alternative)
  (if-not)                   |
                             | (if (condition)    ;; Condition
                             |    (inc a)         ;; True branch
                             |    (inc b))        ;; False branch
                             |
  when (there is no false    | (when (> a 0)
    branch to execute)       |    (println "a > 0")
                             |    (inc a))
                             |
  when-not (there is no true | This convenient macro is an if (without the alternative
    branch to execute)       | clause), along with an implicit do. This allows
                             | multiple s-expressions to be passed in as the body.
                             |
                             | (when-not (> a 0)
                             |    (println "a <= 0")
                             |    (dec a))
                             |
                             |
  Case Expression            | (case x           ;; "x" is the Expression to match
                             |    10 :ten        ;;  case :result
                             |    20 :twenty     ;;  case :result
                             |    50 :fifty      ;;  case :result
                             |    :other)        ;; Default result expression
                             |
  Cond expression            | Cond allows you to flatten nested trees of if
                             | conditionals. The general form looks like:
                             |
                             | (cond & clauses)
                             |
                             |
                             | (def x 1)
                             |
                             | (cond
                             |   (> x 0 ) "greater!"
                             |   (= x 0)  "zero!"
                             |   :default "lesser!"
                             |
                             | ;=> "greater!"
                             |
  Do                         | To combine multiple s-expression into a single
                             | form, Clojure provides the do form. It can be used
                             | for any situation where some side effect is desired
                             | and the higher-order form accepts only a sing
                             | s-expression
                             |
                             | ( if (is-something-true?)
                             |   (do
                             |     (log-message "in true branch")
                             |     (store-something-in-db)
                             |     (return-useful-value)))
``` 
## Logical functions
```
  and                        | "and" returns the first failing value. If all
                             | objects are "Truthy" it will return the last
                             | value
                             |
                             | (and :a :b :c)      ;; NOTE: only nil and false
                             | ;=> :c                 are logically false;
                             |                        everything else is true
                             | (and :a nil :c)
                             | ;=> nil
                             |
  or                         | "or" works in the opposite way. If any values
                             | return true, it returns it as the value of the or
                             |
                             | (or)
                             | ;=> nil
                             |
                             | (or :a nil :c)
                             | ;=> :a
                             |
                             | (or nil false)
                             | ;=> false
                             |
                             | (or false nil)
                             | ;=> nil
                             |
  not                        | "not" function inverts the logical value of
                             | whateveris passed in as a nargument.
                             |
                             | (not true)
                             | ;=> false
                             |
                             | (not nil)
                             | ;=> true
```
# Reader Macros
```
  Quote (')                  | Quotes theform follwing it, same as (quote)     
  Character (\)              | Yields a character literal                      
  Comment (;)                | Single-line comment                             
  Meta (^)                   | Associates metadata for the form that follows it
  Deref (@)                  | Dereferences the agent or ref that follows      
  Dispatch (#)               | #{} Constructs a set                            
                             | #"" Constructs a regex patter                   
                             | #^ Associates metadata for the form that follows
                             | #' REsolves the var for the symbol that follows,
                             | #_ Skips the following form                     
 Syntax quote (`)            | Used in macros to render s-expressions
  Unquote (~)                | Unquotes forms inside syntax-quoted forms       
  Unquote splice (~@)        | Unquotes a list inside a syntax form, but insert
                             |   the elements of the list without the surroundi
```

## Functional iteration
```
(loops / recursion)          |
                             |
  while                      | Clojure's while macro works in a similar fashion
                             | to those seen in imperative languages
                             |
                             | (while test & body)
                             |
                             | (while (request-on-queue?)
                             |   (handle-request (pop-request-queue)))
                             |
  LOOP/RECUR                 |
                             |
  loop                       | (loop bindings & body)  <- general form
                             |
                             | (defn fact-loop [n]
                             |   (loop [current n fact 1]
                             |     (if (= current 1)
                             |       fact                                           <- Return whatever value fact ends up having when current is 1
                             |         (recure (dec current) (* fact current) ))))  <- But if current isn't 1, repeat the loop with current resets
                             |                                                         to current minus 1 and with fact set to current times fact
                             |
  recure                     | (recur bindings)  <- general form
                             |   ;; NOTE: in recur, the bindings are computed,
                             |            and each value is bound to the respective
                             |            name as described in the loop form.
                             |            Execution then returns to the start of
                             |            the loop body.
                             |
                             |   ;; recur can only be used in the tail position
                             |      of the loop (last to evaluate)
                             |
  DOSEQ AND DOTIMES          |
  doseq                      | (defn run-report [user]
                             |   (println "Running report for" user))
                             |
                             | (defn dispatch-reporting-jobs [all-users]
                             |   (doseq [user all-users]
                             |     (run-report user)))
                             |
                             | The simplest form accepts a vector containing two
                             | terms, where the first term is a new symbol, which
                             | will be sequentially bound to each element in the
                             | secound term (which must be a squence). The body
                             | will be executed for each element in the sequence
                             | and then the entire form will return nil.
                             |
  dotimes                    | (dotimes [x 5]
                             |   (println "x is" x))
                             |
                             | dotimes is similar. It's a convenience macro that
                             | accepts a vector containing a symbol and a number n,
                             | followed by e body. The symbol is set to numbers from
                             | 0 to (n - 1), and the body is evaluated for each number
                             |
  map                        | The simplest use of map accepts a unary function and
                             | a sequence of data elements. map applies tis function
                             | to each element of the sequence and returns a new sequence
                             | that contains all the returned values.
                             |
                             | (map inc [0 1 2 3])
                             | ;=> (1 2 3 4)
                             |
                             | map accepts a function that can take any number of
                             | arguments, along with the same number of sequences.
                             | It collects the result of applying the function to
                             | corresponding elements from each sequence
                             |
                             | (map + [0 1 2 3] [0 1 2 3])  ->  When supplying multiple sequences, each
                             | ;=> (0 2 4 6)                    supplies an additional argument to function
                             |
                             | (map + [0 1 2 3] [0 1 2])  ->  Length of return value is
                             | ;=> (0 2 4)                    length of shortest sequence.
                             |
  FILTER AND REMOVE          |
  filter                     | filter does something similar to map - it collects values.
                             | But it accepts a predicate function and a squence and
                             | returns only those elements of the sequence that retrun
                             | a logically true value when the predicate function is
                             | called on them.
                             |
                             | (defn non-zero-expenses [expenses]
                             |   (let [non-zero? (fn [e] (not (zero? e)))]
                             |     (filter non-zero? expenes)))
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             | (for [i [1 2 3]]
                             |    (inc 1))        ;; Output: (2 3 4)
                             |
```
## The Dot and new operators
```
 The dot operator, written as a literal ".", forms
 the basis for Java interop. When seen by itself
 after an opening parenthesis, it should be read a
 "in the scope of A do B with arguments..." for example

   (. Math PI)
   ;; Result: 3.141592653589793
   (. Math abs -3)
   ;; Result: 3
   (. "foo" toUpperCase)
   ;; Result: "FOO"

 To create instance of classes, you can use the
 the new operator or a trailing dot to indicate
 that the class's constructor should be called

 (new Integer "42")
 ;; Result: 42
 (Integer. "42")
 ;; Result: 42
```
