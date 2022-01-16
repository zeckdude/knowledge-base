## Web Development

### Quick Reference Notes

| Term | Definition | Example |
| --- | --- | --- |


<br>

### Notes

Ways to make website load faster
1. Use a server that's close to the user
2. Limit number of requests
  - Host own fonts
3. Size of files
  - Minify CSS
  - 

DOCTYPE tells the browser which version of HTML the site is using so the website loads properly.

Which CSS selectors win
- Specificity
- Importance (!important keyword)
- Source order (later styles of the same specificity and importance win)

px vs em vs rem
- px: Actual pixels
- em: Multiplier based on the font-size of the parent element
- rem: Multiplier based on the font-size on the html element

Arguments vs parameter
- arguments: values passed to a function
- parameters: values available inside a function as defined variables

#### How JavaScript is understood by the computer
  - JavaScript can execute on any device that has a JavaScript engine, such as the browser and server.
  - A computer doesn't understand Javascript code, but rather only reads binary code.
  - Browsers have embedded engines called a "JavaScript virtual machine" which converts the Javascript to the binary machine code that the computer understands.
    - Chrome and Opera - V8
    - SpiderMonkey - Firefox
    - Different versions of IE - Trident or Chakra
    - Microsoft Edge - ChakraCore
    - Safari - SquirrelFish
  - The JS engines follow a series of steps to create the binary machine code (example is the flow of the V8 engine):
<img width="1669" alt="Screen Shot 2022-01-02 at 11 51 39 PM" src="https://user-images.githubusercontent.com/947856/149642553-b0a99716-e1e3-4254-8e9f-710e501c7f45.png">

  1. Parser: Parse JS code
  2. AST: Break JS down into AST (Abstract syntax tree) format which helps the engine to understand what's happening in the code that it is parsing
   * [Example](https://astexplorer.net/#/gist/a2d2216ee7a73ee72acebcd41a924bea/4ae1cf56120fd059d0bdffda31fff286f242fabf)
  3. Interpreter: 

  > Extra Info: For the V8 engine by Google, the various parts of the engine have names<br />
  > Interpreter: Ignition
  > Compiler: TurboFan


 
 
 


