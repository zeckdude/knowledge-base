## JavaScript Engine

### Resources
 - https://www.udemy.com/course/advanced-javascript-concepts
 - https://medium.com/dailyjs/understanding-v8s-bytecode-317d46c94775
 - https://felixgerschau.com/javascript-event-loop-call-stack/
 - https://felixgerschau.com/javascript-memory-management/
 - https://medium.com/@allansendagi/javascript-fundamentals-call-stack-and-memory-heap-401eb8713204
 - https://levelup.gitconnected.com/understanding-call-stack-and-heap-memory-in-js-e34bf8d3c3a4
 - https://javascript.info/garbage-collection

### How JavaScript is understood by the computer
<img width="233" alt="Screen Shot 2022-01-21 at 1 28 44 AM" src="https://user-images.githubusercontent.com/947856/150585014-9bf7fa46-1524-4b79-9eb0-f408e4b525aa.png">

  - JavaScript can execute on any device that has a JavaScript engine, such as the browser and server.
  - A computer doesn't understand Javascript code, but rather only reads binary code.
  - Browsers have embedded engines called a "JavaScript virtual machine" which converts the Javascript to the binary machine code that the computer understands.
    - Chrome and Opera - V8
    - SpiderMonkey - Firefox
    - Different versions of IE - Trident or Chakra
    - Microsoft Edge - ChakraCore
    - Safari - SquirrelFish
<br /><br />
    > JavaScript is defined by the EcmaScript standard and EcmaScript is defined by the TC-39 committee, which discusses additions/changes to the language and formalize it as a standard. The browser engine companies then implement that standard when analyzing JavaScript.

  - The JS engines follow a series of steps to create the binary machine code (example is the flow of the V8 engine):
<img width="1669" alt="Screen Shot 2022-01-02 at 11 51 39 PM" src="https://user-images.githubusercontent.com/947856/149642553-b0a99716-e1e3-4254-8e9f-710e501c7f45.png">

   1. `Parser`: Parse JS code
   2. `AST`: Break JS down into AST (Abstract syntax tree) format which helps the engine to understand what's happening in the code that it is parsing
     - [Example](https://astexplorer.net/#/gist/a2d2216ee7a73ee72acebcd41a924bea/4ae1cf56120fd059d0bdffda31fff286f242fabf)
   3. `Interpreter`: Generates bytecode from the AST. Bytecode is an abstraction of machine code. It is able to be executed by the JS engine to run the program.
   4. `Profiler (Monitor)`: It observes the code that is run through the interpreter and looks for code that can be optimized via the compiler.
   5. `Compiler` or `JIT compiler` (just in time): Compiles bytecode that can be optimized into machine code and uses the machine code for those areas going forward. The machine code will perform faster than the bytecode. 
   6. The end result is the JavaScript engine running a mixture of bytecode and machine code to achieve fast performance.

  > For the V8 engine by Google, the various parts of the engine have names:<br />
  > Interpreter: Ignition<br />
  > Compiler: TurboFan


### Call stack
![2022-01-21 00 03 08](https://user-images.githubusercontent.com/947856/150489957-5aea5fb1-3db9-45ec-92bf-e0bff0bac8ea.gif)

- Where the engine keeps track of where the code is in its execution. It is a mechanism that helps the JavaScript interpreter to keep track of the functions that a script calls.

  > Note: JavaScript is a single-threaded which means it can only perform one command at a time 

  - When a function is called it is added to the call stack in the order of which it was called. 
  - When a function calls other functions those other functions are added to the top of the call stack. 
  - The latest functions that are called are executed first. 
  - When a function is completed (either returns a value or reaches the end of the function) then it is removed from the call stack.
  - This repeats until the first function that was called is completed. This approach is called the Last In, First Out principle.
  - In addition to storing references to function calls, the call stack also stores all primitive values (string, number, boolean, undefined, null, and symbol)
  - It is allocated a fixed amount of memory for each value

### Memory heap
<img width="580" alt="Screen Shot 2022-01-21 at 1 10 37 AM" src="https://user-images.githubusercontent.com/947856/150499455-5730e3df-6185-4b29-9b65-d4729513b46f.png">

- Where the memory allocation for objects (all non-primitives) happens on the client's machine

  > Note: When we create variables, functions, or anything you can think of, the JS engine allocates memory for this and releases it once it's not needed anymore 
  - When a variable or function is created, it is temporarily stored in the memory heap which is a part of the system memory that is allocated to the JavaScript engine
  - The stored data in memory has an address that the variable/function maps to. When we use a variable in the code, we are accessing the value that is stored at the address associated with the variable name.
  - Unlike the call stack, in the heap each stored value isn't allocated a fixed amount of memory. Instead, more space gets allocated as needed.
 
  <br />
      <img width="521" alt="Screen Shot 2022-01-21 at 1 18 04 AM" src="https://user-images.githubusercontent.com/947856/150500551-2d68b9a1-a625-42c4-86f9-9bff1938f038.png">


 
 ### Stack overflow
 <img width="731" alt="Screen Shot 2022-01-21 at 1 25 22 AM" src="https://user-images.githubusercontent.com/947856/150501731-05fdecd8-69c3-4eb6-aede-b88912881256.png">
 
 - An error that is caused when a program tries to use more space than the call stack has allocated. This is commonly caused by a recursive function and you’ll see the error `Maximum call stack size exceeded`.
 - The maximum call stack size ranges from 10 to 50 thousand calls, so if you exceed that, it's most likely that you have an infinite loop in your code.
 - The browser prevents your code from freezing the whole page by limiting the call stack.
 - A way to prevent this is by either not using recursive functions in the first place or by providing a base case, which makes your function exit at some point.

 ### Garbage collection
 - Process that is automatically handled by the JS engine in which it releases memory for variables or functions that are no longer needed
 - This frees up memory for other data to be stored
 - The way that the garbage collector determines that something is still needed in memory, and will not be released, is determined if a value is "reachable", which means they are accessible or usable somehow. They are guaranteed to be stored in memory.
 - A value is considered reachable, when it meets any of the following criteria:
   - The currently executing function, its local variables and parameters
   - Other functions on the current chain of nested calls, their local variables and parameters
   - Global variables
   - (there are some other, internal ones as well)
   - if it’s reachable from a root (any of the previously mentioned reachable values) by a reference or by a chain of references.

  > Note: The algorithm that the garbage collector uses which determines if a value is reachable from the root object (window on browser or global on node) is determined by the Mark-and-sweep algorithm which is used in all modern browsers

  <!-- ### Memory leak -->
  Woah this is cool



 



