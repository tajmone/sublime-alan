# Sublime-Alan TODOs

Pending tasks and bugs list.


-----

**Table of Contents**

<!-- MarkdownTOC autolink="true" bracket="round" autoanchor="false" lowercase="only_ascii" uri_encoding="true" levels="1,2,3" -->

- [TODOs](#todos)
    - [Alan Syntax Fixes](#alan-syntax-fixes)
    - [Syntax Test Files](#syntax-test-files)
    - [Build Systems](#build-systems)
    - [Build System Compiler Sytnax](#build-system-compiler-sytnax)
        - [AlanLog Color Scheme](#alanlog-color-scheme)
    - [Snippets](#snippets)
- [Bugs](#bugs)
- [Fixed Bugs](#fixed-bugs)
    - [Syntax](#syntax)

<!-- /MarkdownTOC -->

-----

# TODOs

List of planned tasks and features:

- [ ] Add some snippets:
    + [x] `abp` » Alan Boilerplate (barebones template for Alan code).
    + [x] `newadv` » New Adventure Boilerplate (Alan StdLib)
    + [ ] Commented Header Frame
- [ ] Create dedicate Alan color schemes:
    + [x] A dark scheme: "__Alan DarkFluo__"
    + [ ] A light scheme.
    + [ ] Scheme for testing Alan syntax (color everything)
- [x] Implement indexing for Goto funcionality:
    + [ ] Indexed elements:
        * [x] Class names (declarations)
        * [x] Instance names (declarations)
        * [ ] Verbs
        * [ ] Syntaxes
    + [x] __Quoted identifiers__ transformations:
        * [x] strip single quote delimiters
        * [x] replace double SQuote (escaped) qith single quote
- [ ] Implement autocompletion

## Alan Syntax Fixes

+ [ ] __Quoted Identifiers__:
    * [ ] Add `empty` scope to empty identifiers?
    * [x] Cleanup __quoted identifiers__ code, along the lines of Strings, and make sure it can handle `'..''''..'`
- [ ] Decide semantic scope for identifiers:
    + [x] Class: `entity.name.class`
    + [x] Class name repeated after `END`: `entity.name.class.tail.alan`
    + [x] Inherited Class: `entity.other.inherited-class`
+ [ ] __Special $ Characters__:
    * [ ] The parameters $ Chars (`$1`, etc.) should be scoped as _placeholders_:

        ```
        constant.other.placeholder
        ```

        (they resemble more the ` %s` in `sprintf()` rather than escape sequences)

## Syntax Test Files

Add [syntax test files][ST3Docs syntax test] to [`/tests/`][tests]:

+ [x] __Strings__:
    * [`syntax_test_Strings.alan`][test_Strings] (__OK!__)
+ [x] __Quoted Identifiers__:
    * [`syntax_test_QuotedIdentifiers.alan`][test_QuotedIdentifiers] (__OK!__)
+ [ ] __Comments__
+ [ ] __Keywords__
+ [ ] __Special $ Characters__


[ST3Docs syntax test]: https://www.sublimetext.com/docs/3/syntax.html#testing "See Sublime Text 3 official documentation for this topic"

[tests]: ./tests/ "See 'tests' folder"
[test_Strings]: ./tests/syntax_test_Strings.alan "Open file..."
[test_QuotedIdentifiers]: ./tests/syntax_test_QuotedIdentifiers.alan "Open file..."

## Build Systems

Add cross-platform [build systems][ST3Docs BuildSys] (alan compiler must be available on path.

> NOTE — the `-ide` options reports the error line, but instead of the column it reports the range of chars offset (relative the beginning of file) of the problematic code. The `-cc` option reports line and column instead (eg `line 5(24)`).

- [x] default build:
    + [x] use options:
        * [x] `-cc`
    + [x] implement navigating results
    + [x] color highlight compiler's output in ST's console

[ST3Docs BuildSys]: http://www.sublimetext.com/docs/3/build_systems.html "See Sublime Text 3 official documentation for this topic"

## Build System Compiler Sytnax

The Build system's __AlanLog__ syntax and color scheme.

- [ ] Fix scope nameing with more appropriate names.
- [ ] Cover also these error types:
    + [ ] `I` — Information (not an error; so, blue BG?)
    + [ ] `F` — (fix it) the "F" doesn't stand for "File" but for "Fatal" (finx scope name in syntax and color scheme)
    + [ ] `S` — system.

### AlanLog Color Scheme

- [ ] Fix colors

## Snippets

Create some useful snippets.

- [x] New Adventure Boilerplate (StdLib).

# Bugs

Known bugs which need fixing:

# Fixed Bugs

## Syntax


- [x]  __Inconsistent scoping of Quoted identifiers sinqgle-quote delimiters__ — Some class symbols quoted identifiers are scoped without the delimiting quotes (eg: `inherited_class_identifier`), while others include them. This is due to the reusable `generic_identifier` introduced lately, which leverages being included in a (optional) `set` context that uses `scope_meta` to scope it to the current need. The previous system of using context variants for each identifier, had the advantage of allowing to leave out the delimiting SQ symbols from the `entity.name`. ~~It looks like I'll have to switch back to the old system at the cost of redundancy, having to create multiple identifiers, one for each specific scope (inherited class, class, class tail, and so on)~~.

      __*Fixed*__ (`2018-04-29`)

      Now delimiting quotes will always be scoped as part of the identifier; they just get the additional `punctuation.definition.identifier.alan` scope. This simplifies reusable contexts; also, it seems appropriate. Of course, in the Goto Symbol functionality, all quoted identifiers are indexed without the delimiting quotes, and with all internal escaped quotes (ie `''`) shown as a single quote. This simplifies fuzzy search of the identifier, and is also how the identifier is actually rendered in the game world.


- [x] __Strings__: two consecutive escaped DQs in the middle of a string prematurely end the string:

      ```
      "Enclose in double quotes ("""") what you want to say.".
      ```

      ... strings ends at `("""` and `") what` is treated as normal text.

      __*Fixed*__ (`2018-04-14:3`)

      Now the test file [`syntax_test_Strings.alan`][test_Strings] succeeds.
