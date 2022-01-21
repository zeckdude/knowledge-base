## JavaScript Engine

### Resources
 - https://www.udemy.com/course/advanced-javascript-concepts
 - https://medium.com/dailyjs/understanding-v8s-bytecode-317d46c94775
 - https://felixgerschau.com/javascript-event-loop-call-stack/

### How JavaScript is understood by the computer
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
   5. `Compiler` or `JIT compiler (just in time): Compiles bytecode that can be optimized into machine code and uses the machine code for those areas going forward. The machine code will perform faster than the bytecode. 
   6. The end result is the JavaScript engine running a mixture of bytecode and machine code to achieve fast performance.

  > For the V8 engine by Google, the various parts of the engine have names:<br />
  > Interpreter: Ignition<br />
  > Compiler: TurboFan


### Call stack
![2022-01-21 00 03 08](https://user-images.githubusercontent.com/947856/150489957-5aea5fb1-3db9-45ec-92bf-e0bff0bac8ea.gif)

- Call Stack: Where the engine keeps track of where the code is in its execution
  - 
  - When a function is called 

### Memory heap
- Memory Heap: Where the memory allocation happens on the client's machine
  - When a variable or function is created, it is temporarily stored in the memory heap which is a part of the system memory that is allocated to the JavaScript engine
  - The thing in memory has an address that the variable/function maps to

 
 
 


