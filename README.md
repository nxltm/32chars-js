# PunkScript

PunkScript is a minimal JavaScript obfuscator that encodes JavaScript or any piece of text into heavily obfuscated JavaScript code, completely devoid of all numbers and letters.

This project is the spiritual successor to Yosuke Hasegawa's [jjencode](https://utf-8.jp/public/jjencode.html) and the polar opposite of [JSF\*ck](https://github.com/aemkei/jsfuck).

This version also uses modern (ES6) syntax and features, such as string interpolation, tagged templates and calculated properties, to significantly shorten the generated output.

This project is almost finished and is yet in the process of being converted into a CLI and Node API. A second project, titled ChaosScript, will be made in the near future.

## Key features

- Only 32 ASCII symbol and punctuation characters, nothing more, nothing less
- A single global variable (which you can customize)
- Different types of quoting styles _(Adding backtick support in future)_:
  - single/double quoted only
  - cycle-quote
  - smart-quote (Prettier-style)
  - random-quoting
- Fast-as-possible encoding
  - [1,167,707 characters](https://raw.githubusercontent.com/nxltm/PunkScript/main/input.txt)
  - [3,022,630 char output](https://raw.githubusercontent.com/nxltm/PunkScript/main/output.js) - 2,544,260 expression output
  - 2.18 I/O ratio
  - 3.548s fastest runtime
- Generated code can be run even on a browser!

## Disclaimer

**ONLY OBFUSCATE THINGS THAT BELONG TO YOU**. This repository and command line program shall not be used nor intended for malicious purposes, including scripting attacks, since it is a code obfuscator and can bypass most filters. I strongly urge you **NOT** to use this program to generate ANY malicious JavaScript code, or run programs that would otherwise generate such code.

This program shall ONLY be used for experimental, educational and privacy purposes. **I am absolutely NOT responsible for any damage caused by the generated code or the program itself.**

## Frequently Asked Questions

#### Why would I want to obfuscate my JavaScript code?

There are numerous reasons why it's a good idea to protect your code, such as to prevent anyone from copying/pasting your work. This is especially important on private works, such as client-side games, command-line interfaces, and anything involving plain text such as manuscripts.

#### Is this obfuscator absolutely foolproof?

This obfuscator decrypts itself only when run in a Node.JS environment, so it can only be considered a step in the process if you really want maximum privacy. And because there is a one to one correspondence between the sequence of substrings in the input and output, the source can obviously be recovered; it may not be obvious.

#### Why is my obfuscated code larger than my original source?

Because there are only 32 different kinds of characters in the output, the ratio of input to output depends heavily on the types of characters that are available in the input and how often these sequences occur.

Sequences of any of these 32 symbol or punctuation characters are encoded literally in the string, they get a 1-to-1 encoding except for escape sequences `\`, `\'`, `\"` and `` \` ``. Spaces have a 1-to-1 correspondence because they are encoded as commas.

Words, numbers and other alphanumerics are encoded once and stored in the global object, so any repeat sequence of any of these would only be encoded as a property of the global object.

You don't have to worry too much about code size because there is a lot of repetition and only 32 characters.

#### Can I run a minifier or prettifier such as Prettier or UglifyJS on the obfuscated output?

No for most cases, except for small inputs of probably a few thousand words. Since there are many tokens in the output, it would probably break your formatter or minifier or whatever is used to display your result.

## Fixes and bugs

- Turn the source code into a CLI application
- Refactor obfuscator function to work with the new `options` object
- Add support for:
  - Template string quoting
  - Template string interpolation
  - Array joining (commas are excluded because of `toString()`)

## Installation

### Using NPM

Install the package with NPM and add it to your `dependencies`:

```bash
$ npm install --save void-script
```

### In a browser environment

From CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/void-script/dist/index.browser.js"></script>
```

From `node_modules`:

```html
<script src="./node_modules/void-script/dist/index.browser.js"></script>
```

## Usage

```js
const PunkScript = require("void-script")
var obfuscatedResult = PunkScript.encode(
  "a=>a.split`,`.map(a=>parseInt([...a].map\
(a=>[...Array(+(31)).keys()].map(a=>a.toString(31))\
[CIPHER_TO.indexOf(a)]).join``,31))\
.map(a=>String.fromCharCode(a)).join``"
)
```

Yes, this statement is built programmatically.

<!-- prettier-ignore -->
```js
var __,_=~[];_={___:`${++_}`,'_$':`${!''}`[_],'_-':`${![]}`[_],'$/':`${!''/![]}`[_],'$%':`${+{}}`[_],__$:`${++_}`,'_|':`${!''}`[_],'_;':`${![]}`[_],'_%':`${[][[]]}`[_],'_&':`${{}}`[_],_$_:`${++_}`,'_=':`${!''}`[_],'_+':`${![]}`[_],'_:':`${[][[]]}`[_],'_.':`${{}}`[_],_$$:`${++_}`,'__':`${!''}`[_],'_~':`${![]}`[_],"_'":`${{}}`[_],$__:`${++_}`,$_$:`${++_}`,'_/':`${[][[]]}`[_],'_!':`${{}}`[_],$$_:`${++_}`,$$$:`${++_}`,'_@':`${!''/![]}`[_],'-':`${{}}`[_],$___:`${++_}`,'$&':`${{}}`[_],$__$:`${++_}`};_={..._,'+':_['_!']+_['_&']+_['_%']+_['_!']+_['_;']+_._$,'!':_['_!']+_['_;']+_['_+']+_['_+'],'%':_["_'"]+_['_&']+_['_/']+_['_%'],'/':_['_~']+_['_+']+_['_/']+_['_!']+_.__,_:_['_|']+_.__+_._$+_['_=']+_['_|']+_['_%'],$:_['_!']+_['_&']+_['_%']+_['_~']+_._$+_['_|']+_['_=']+_['_!']+_._$+_['_&']+_['_|']};_={..._,'$;':`${[][_.$]}`[_.$__$],'_<':`${[][_.$]}`[_._$_+_.$__],'$~':`${''[_.$]}`[_.$__$],'_,':`${''[_.$]}`[_.__$+_.$__],'_#':`${(~[])[_.$]}`[_.__$+_.__$],'$.':`${(![])[_.$]}`[_.$__$],'$|':`${/./[_.$]}`[_.$__$],'$_':`${/./[_.$]}`[_.__$+_._$_],'_`':`${/./[_.$]}`[_.__$+_._$$],'_^':`${/./[_.$]}`[_.__$+_.$__],'$-':`${(()=>{})[_.$]}`[_.$__$]};_={..._,'?':_['_%']+_['_;']+_['_#']+_.__,'^':_['_#']+_['_;']+_['_^'],':':_['_|']+_.__+_['_^']+_['_+']+_['_;']+_['_!']+_.__,'*':_['_|']+_.__+_['_^']+_.__+_['_;']+_._$,'|':_['_~']+_['_^']+_['_+']+_['_/']+_._$,'#':_['_/']+_['_%']+_['_:']+_.__+_['_`']+_['$&']+_['_-'],'`':_['_~']+_['_&']+_['_=']+_['_|']+_['_!']+_.__};_={..._,'=':(()=>{})[_.$](_._+_['-']+_.__+_['_<']+_['_;']+_['_+'])(),'>':(()=>{})[_.$](_._+_['-']+_.__+_['_~']+_['_!']+_['_;']+_['_^']+_.__)(),'<':(()=>{})[_.$](_._+_['-']+_['_=']+_['_%']+_.__+_['_~']+_['_!']+_['_;']+_['_^']+_.__)(),'~':(()=>{})[_.$](_._+_['-']+_['_^']+_['_;']+_['_|']+_['_~']+_.__+_['$/']+_['_%']+_._$)()};_={..._,"'":_._$+_['_&']+''[_.$][_['?']],'$!':_['>']('<')[_._$_],'$:':_['>']('=')[_._$_]};_={..._,'$=':`${{}[_["'"]][_['!']]()}`[_.$___],'_?':(+(_.__$+_.$$$))[_["'"]](_._$$+_.$$_),'_*':(+(_._$_+_.___))[_["'"]](_._$$+_.$$_),'_"':(+(_._$_+_.$$_))[_["'"]](_._$$+_.$$_),'_>':(+(_._$$+_._$_))[_["'"]](_._$$+_.$$_),'_\\':(+(_._$$+_.$_$))[_["'"]](_._$$+_.$$_)};_={..._,'@':_['_-']+_['_|']+_['_&']+_['_#']+_['$!']+_['_?']+_['_;']+_['_|']+_['$!']+_['_&']+_['_:']+_.__,'&':_['_*']+_.__+_['_@']+_['_~'],'"':_._$+_['_&']+_['$=']+_['_^']+_['_^']+_.__+_['_|']+_['$!']+_['_;']+_['_~']+_.__};_[+![]]=__=>__[_['|']]`,`[_['^']](__=>_['~']([...__][_['^']](__=>[...[][_.$](+(_._$$+_.__$))[_['&']]()][_['^']](__=>__[_["'"]](_._$$+_.__$))['_.:;!?*+^-=<>~\'"/|#$%&@{}()[]`\\'[_['#']](__)])[_['%']]``,_._$$+_.__$))[_['^']](__=>''[_.$][_['@']](__))[_['%']]``;_={..._,'(':_[+![]]('.%,.#'),')':_[+![]](';$,;!,;&,;@,;^,:<,;|,;{'),'[':_[+![]](':;,;&,;&,;!,;]'),']':_[+![]](';{,;#,:&,;{,;&,;>,;|,;='),'{':_[+![]](':?,:<,:#,:=,:+,:%'),'}':_[+![]](':@'),'..':_[+![]](':&,;{,;&,;>,;|,;=')};__=[_['_;']+'=>'+_['_;']+'.'+_['|']+'`,`.'+_['^']+'('+_['_;']+'=>'+_[')']+'([...'+_['_;']+'].'+_['^']+'('+_['_;']+'=>[...'+[][_.$][_['?']]+'(+('+_['(']+')).'+_['&']+'()].'+_['^']+'('+_['_;']+'=>'+_['_;']+'.'+_[']']+'('+_['(']+'))['+_['{']+'_'+_['}']+_[+![]](':|')+'.'+_['#']+'('+_['_;']+')]).'+_['%']+'``,'+_['(']+')).'+_['^']+'('+_['_;']+'=>'+''[_.$][_['?']]+'.'+_['@']+'('+_['_;']+')).'+_['%']+'``'][_['%']](_['-']);module['exports']['result']=__
```

PunkScript has only one function `encode(text, options)`, which returns a `String` containing the obfuscated code.

#### Options

```js
;({
  prettier: false,
  declaration: "var",
  shebang: false,
  strict: true,
  iife: true,
  quoteStyle: {
    quoteSequence: ["single", "double"],
    quoteMode: "smart",
  },
  expressionStyle: "concat",
})
```

- `prettier: boolean`: Returns a pretty-printed version of the output string
- `declaration: 'none'|'var'|'let'`: Includes a variable declaration statement. Used only when option `strict` is enabled.
- `shebang: boolean`: Outputs a shell shebang statement.
- `strict: boolean`: Outputs `'use strict'` as the program header.
- `iife: boolean`: Wraps output in an IIFE.
- `quoteStyle`: An object containing the quoting style to use throughout the document.
  - `quoteSequence: 'single'|'double'|'backtick'|('single'|'double'|'backtick')[]`: A sequence of quoting styles.
  - `quoteMode: 'only'|'cycle'|'smart'|'random'`:
    - `only`: Uses only that quoting style throughout the document.
    - `cycle`: Cycles between quotes as defined in `sequence`
    - `smart`: Optimizes and overrides the current quoting style to return the minimal output. Falls back to the next if output is longer.
    - `random`: Randomizes quoting style. Uses `Math#random` under the hood.
- `expressionStyle: 'concat'|'array'|'template'`: Whether to use string concatenation, array joining or interpolation to join substrings together.
  - `concat`: Uses the `+` operator to concatenate strings.
  - `template`: Embeds sub-expressions in template strings while symbol characters are encoded literally inside the template string.
  - `array`: Separates all substrings with commas and embeds it in an array.
- `export: string` Include a `module.exports` statement with a custom key for the output string. For use only in Node.

String options are case-insensitive.

## How it works

Like JJEncode, PunkScript is a substitution encoding scheme that goes through three phases:

- Initialization, where characters and values are assigned to variables;
- Substitution, where the variables are used to construct strings;
- Execution, where the constructed code is evaluated and executed.

You may want to read [this article](https://blog.korelogic.com/blog/2015/01/12/javascript_deobfuscation) explaining how the original jjencode works, along with the main key differences between PunkScript and jjencode.

The entire file is generated with the same [program I made](https://github.com/nxltm/PunkScript/blob/main/obfuscator.js); do take note I used experimental JavaScript syntax, which is run using a special BabelJS configuration (see `package.json`).

---

The obfuscator/encoder works by heavily abusing JavaScript's weird quirks, including its infamous type coercion feature. JavaScript is a weakly typed programming language, and it allows the evaluation of any expression as any type.

It's weird enough that you could write an entire valid JavaScript program or virtually any piece of text with as little as six characters. This project uses a substantial character pool of 32, which are the symbol and punctuation characters in ASCII, nothing more, nothing less.

This program is a superset of jjencode in that regard and many concepts behind jjencode have also been adopted in PunkScript. There is a single global variable (default `$`) which stores strings and functions, with a second storing the encoded input string as an obfuscated JavaScript expression.

Both are essentially a substitution encoding that goes through two phases: initialization, where characters and substrings are assigned to values, and substitution, where the variables are used to construct back the input string. There might be a third phase, execution, which is done by passing the code (evaluating to a string) to the Function constructor to be executed as JavaScript.

I assign the global variable `$` to `~[]`, made by getting the bitwise NOT of an empty array. We then increment this variable and begin assigning properties into an object by accessing single characters of simple boolean, numeric or primitive values as strings: `true`, `false`, `undefined`, `Infinity`, `NaN`, and `[object Object]`, making to cipher our properties so we can access them later. In the same statement, we then reassign that object to the global variable.

I assign the letters with two characters, the first which defines the case and the second the actual letter. The numbers have keys defined as binary.

I then use these letters to begin assembling strings such as `constructor`, and we can turn them into strings by converting its constructor into a string, to give us a string like `function Array() { [native code] }`, yielding us a few more letters. This includes the new Function literal, `()=>{}`.

In between every step, I then start forming the names of methods and functions with these single-letter strings, and along the way retrieving global functions such as `eval`, `escape` and `parseInt` with the Function constructor. I assign single symbol keys to these strings so I could use them to access properties and call methods easier.

Now we have almost the entire lowercase alphabet save for a few and about half of the uppercase letters. The other five lowercase letters (`hkqwz`) are made by converting a small number into a base 36 string which always yields lowercase. Two more uppercase letters `C` and `D` are created by escaping a URL with a single character, and uppercase `U` is gotten from the `[object Undefined]` string.

Using the strings I made, I define a pair of functions that turn arbitrary UTF-16 sequences into a sequence of symbol characters. (The decoder function is ciphered). The code points are converted into base 31 and its digits ciphered using the 31 symbol characters, leaving the comma to separate each UTF-16 code unit.

Words that repeat themselves throughout the program are captured, encoded and assigned new keys to the same global object, ranked based on decreasing frequency and given a predefined key based on a custom generator function so that they can be referenced in the string later on. Exceptions to this include the single character strings, stringified primitives and literals, and the property and method strings which have been defined already.

Sequences of ASCII symbols are included literally in the output. A regular expression splits and tokenizes the input string into these categories, and then joins them together with a `+` which is the string concatenation operator.

While the output does have some letters and symbols, I left them there mostly for debugging.
