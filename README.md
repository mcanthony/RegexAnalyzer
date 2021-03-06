RegexAnalyzer and RegexComposer
=================================

* A simple Regular Expression Analyzer for PHP, Python, Node/JS, ActionScript (TODO)
* A simple and intuitive Regular Expression Composer for PHP, Python, Node/JS, ActionScript (TODO)


*RegexComposer PHP / Python / ActionScript implementations in progress*

**see also:**  

* [Contemplate](https://github.com/foo123/Contemplate) a light-weight template engine for Node/JS, PHP, Python, ActionScript
* [Tao](https://github.com/foo123/Tao.js) A simple, tiny, isomorphic, precise and fast template engine for handling both string and live dom based templates
* [ModelView](https://github.com/foo123/modelview.js) a light-weight and flexible MVVM framework for JavaScript/HTML5
* [ModelView MVC jQueryUI Widgets](https://github.com/foo123/modelview-widgets) plug-n-play, state-full, full-MVC widgets for jQueryUI using modelview.js (e.g calendars, datepickers, colorpickers, tables/grids, etc..) (in progress)
* [Dromeo](https://github.com/foo123/Dromeo) a flexible, agnostic router for Node/JS, PHP, Python, ActionScript
* [PublishSubscribe](https://github.com/foo123/PublishSubscribe) a simple and flexible publish-subscribe pattern implementation for Node/JS, PHP, Python, ActionScript
* [Xpresion](https://github.com/foo123/Xpresion) a simple and flexible eXpression parser engine (with custom functions and variables support) for PHP, Python, Node/JS, ActionScript
* [Dialect](https://github.com/foo123/Dialect) a simple cross-platform SQL construction for PHP, Python, Node/JS, ActionScript (in progress)
* [Simulacra](https://github.com/foo123/Simulacra) a simulation, algebraic, probability and combinatorics PHP package for scientific computations
* [Asynchronous](https://github.com/foo123/asynchronous.js) a simple manager for async, linearised, parallelised, interleaved and sequential tasks for JavaScript


These are used mostly as parts of other projects but uploaded here as standalone.

The analyzer needs a couple of extensions but overall works good.


See /test/js/test.js under /test folder for examples of how to use


**RegexAnalyzer Live Example:**  

[![Live Example](/test/screenshot.png)](https://foo123.github.com/examples/regex-analyzer/)


**RegexComposer Live Example:**  

[![Live Example](/test/screenshot2.png)](https://foo123.github.com/examples/regex-composer/)


**RegexComposer Example:**  (see /test/js/test.js)

```javascript
var echo = console.log;

echo("Testing Composer");
echo("================");

var Composer = require('../../src/js/RegexComposer.js');
var identifierSubRegex = new Composer( )
                
                .characterGroup( )
                    .characters( '_' )
                    .range( 'a', 'z' )
                .end( )
                
                .characterGroup( )
                    .characters( '_' )
                    .range( 'a', 'z' )
                    .range( '0', '9' )
                .end( )
                
                .zeroOrMore( )
            
                .partial( );

var outregex = new Composer( )
                    
                    .startOfLine( )
                    
                    .either( )
                        
                        .sub( identifierSubRegex )
                        
                        .match( '**aabb**' )
                        
                        .any( )
                        
                        .space( )
                        
                        .digit( false ).oneOrMore( )
                    
                    .end( )
                    
                    .zeroOrMore( false )
                    
                    .endOfLine( )
                    
                    .compose( 'i' );
    
echo("Partial: " + identifierSubRegex);
echo("Composed: " + outregex.toString());
echo("Expected: " + "/^([_a-z][_a-z0-9]*|\\*\\*aabb\\*\\*|.|\\s|\\D+)*?$/i");
echo("================");
echo();
    
```

**Result**

```text

Composed: /^([^abc\.d-f]|\*\*aabb\*\*|.|\s|\D+)*?$/i
Expected: /^([^abc\.d-f]|\*\*aabb\*\*|.|\s|\D+)*?$/i

```