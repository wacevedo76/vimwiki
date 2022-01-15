--------------------------------------------------------------------------------
TypeScript Notes
--------------------------------------------------------------------------------
== Types ==
  any                        | The 'any' type is a dynamic type that can be set
                             | to any other type, it can be set to anything and
                             | reset to anything; The compiler will not warn you
                             | of any issues at runtime.
                             |
                             | This becomes necessary when you do not know where
                             | when the incomming code is coming from a source
                             | that is not under our control, for instance a
                             | different team, an api, or from a different
                             | programmng language.
                             |
                             | It should be used when there are no other alternatives
                             |
  unknown                    |
  (from version 3)           | Similar to the 'any' type, however, any of its
                             | members can not be called or set to another
                             | variable type without first checking what its
                             | type really is. The exception to this rule is
                             | when you set an unknown type to another unknown
                             | type
                             |
  Itersection Types          | The TypeScript compiler focuses on "type shape"
                             |  rantherthan the name of the type. This mechanism
                             |  allows TypeScriptto support what's called
                             | intersection allowing developers to "create
                             | types" by mearning multiple distinct types
                             | together
`                             |  > let obj: { name: string } & { age: number } = {`
`                             |       name: 'tom',`
`                             |       age: 25`
`                             |   }`
`                             | > { name: 'tom', age; 25 }`
                             |
  Union Types                | Similar to the Intersection type, it allows us to
                             | create a type with an either / or assignment
                             |
`                             |   > let unionObj: null | { name: string } = null;`
                             |
  Literal Types              | Literal types are similar to union types, but they
                             | use a set of hardcoded string or number values
`                             |   > let literal: "tom" | "linda" | "jeff" | "sue" = "linda"`
                             | Only the strings defined above will be accepted
                             |
  typeAliasesliase           | It is simply a method to give a different name to
                             | a type and most of the tme it is usd to provide a
                             | shorter simpler name to some complext type
                             |
`                             |   > type Points = 20 | 30 | 40 | 50;`
`                             |   > let score: Points = 20;`
                             |
                             |  Another example of aliases would be for object
                             | literal type declarations:
                             |
`                             |   > type ComplexPerson = {`
`                             |       name: string,`
`                             |       age: number,`
`                             |       birthday: Date,`
`                             |       married: boolean,`
`                             |       address: string,`
`                             |     }`
                             |
== Function return types ==
                             | Function return types come after the function
                             | parameter declaration. If a fuction will not
                             | return anything, a return type can be omitted,
                             | or defind as void
                             |
`                             |     function runMore(distance: number): number {`
`                             |       return distance + 10;`
`                             |     }`
`                             |`
`                             |     function eat(calories: number) {`
`                             |       console.log("I ate " + calories + " calories");`
`                             |     }`
`                             |`
`                             |     function sleepin(hours: number): void {`
`                             |       console.log("I slept " + hours + " hours");`
`                             |     }`
                             |
                             |












