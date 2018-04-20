# Sublime-Alan

- https://github.com/tajmone/sublime-alan

Alan IF 3 syntax for Sublime Text 3.

> __ALPHA STAGE__ — This project is still a WIP Alpha version!

```
Sublime Text >= 3149 (DEV BUILD)
Alan IF v3.0 Beta 5
```

-----

**Table of Contents**

<!-- MarkdownTOC autolink="true" bracket="round" autoanchor="false" lowercase="only_ascii" uri_encoding="true" levels="1,2,3" -->

- [About](#about)
- [Features](#features)
    - [Syntax Highlighting](#syntax-highlighting)
    - [Color Schemes](#color-schemes)
    - [Build Systems](#build-systems)
- [Requirements](#requirements)
- [Installation](#installation)
- [License](#license)
- [Links](#links)

<!-- /MarkdownTOC -->

-----

# About

I've created this Alan 3 syntax package just to add some support for Alan source files in Sublime Text, for my own personal use. I haven't really planned to make this a finished product to share on Package Control. Nevertheless, I've decided to share it publicly — just in case it might be useful to others too, or in the remote chance that someone else will join in the project and give me a hand to flesh it out. 

I'll be polishing the sytnax and adding features as needs arise, and try to document changes. As a guideline, I'll be pushing to `master` only tested features, so you should be safe keeping the package synced to `master` branch. 

# Features

A brief presentation of the features so far implemented.

## Syntax Highlighting

Although the Alan syntax isn't yet fully implemented, it's already mature enough to provide some decent syntax highlighting.

I still need to implement semantic scoping of syntax elements, so that proper indexing can be achieved (Goto functionality, etc.).

For more info on the roadmap and wishlist, see:

- [`TODO.md`][TODO]
- [`CHANGELOG.md`][CHANGELOG]
- [`WORK_NOTES.md`][WORK_NOTES]


## Color Schemes

Sublime-Alan ships with the "__Alan DarkFluo__" color scheme:

![Screenshot of Alan DarkFluo color scheme][Screenshot Alan DarkFluo]

This color scheme is still pretty much work-in-progress. The goal is to provide a palette which doesn't strain the eyes, and where the prose parts of the Alan source stand out from the rest of the code, allowing to easily switch focus between the adventure text and its code.


## Build Systems

The build system allows compiling alan source files directly from within th editor (<kbd>Ctrl</kbd><kbd>B</kbd>). Errors reported by Alan compiler will be overimposed in the sourcecode panel, and the user can navigate through the results via <kbd>F4</kbd> and <kbd>Ctrl</kbd><kbd>F4</kbd>:

![Screenshot of Build system errors navigation in the editor][Screenshot Build Editor]

The full error log from the compiler will also be shown in Sublime Text's console. This package syntax highlights the error log to improve visual navigations of the different error types and messages:

![Screenshot of Build system errors report in Sublime Text console][Screenshot Build Console]

Currently there is only one build system, which compiles the current editor's alan source file  ("`*.alan`" files only) without extra options (except `-cc`, to allow capturing error reports). Additional Build systems will be added soon.

> __NOTE__ — Build functionality requires Alan binary compiler to be available on the system PATH.



# Requirements

Requires __Sublime Text 3__ DEV BUILD `>=3149`.

This package uses some new ST3 features which have not yet been included into the latest stable build (`3143`); so, until the next stable release is out you'll need to use [ST Dev Builds] in order to use this package.

[ST Dev Builds]: https://www.sublimetext.com/3dev "Visit Sublime Text 3 Dev Builds page"

# Installation

Create an "`Alan`" folder inside "`<data_path>/Packages/`", open a shell inside "`<data_path>/Packages/Alan/`" and type:

```
git clone https://github.com/tajmone/sublime-alan .
```

Don't forget the "`.`" after the repository URL! it's needed in order to clone the repository contents directly into the current folder, without creating a "`sublime-alan`" container folder.


# License

- [`LICENSE`](./LICENSE)

```
MIT License

Copyright (c) 2018 Tristano Ajmone
https://github.com/tajmone/sublime-alan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

# Links

Alan IF links:

- [Alan website]
- [IFWiki » Alan page]
- [Alan sourcecode on Bitbucket]
- [Alan Standard Library on Bitbucket]
- [Alan-IF mailing list and discussion group at Yahoo]


[Alan website]: https://www.alanif.se/ "Visit Alan official website"

[Alan sourcecode on Bitbucket]: https://bitbucket.org/alanif/alan
[Alan Standard Library on Bitbucket]: https://bitbucket.org/alanif/alanlib

[Alan-IF mailing list and discussion group at Yahoo]: https://groups.yahoo.com/neo/groups/alan-if/info "Visit Alan-IF discussion group main page at Yahoo Groups"

[IFWiki » Alan page]: http://www.ifwiki.org/index.php/Alan "View Alan entry at IFWiki"

[IFWiki]: http://www.ifwiki.org "Visit IFWiki.org, the Interactive Fiction Wiki"

<!------- OTHER DOC FILES ------->

[TODO]: ./TODO.md "View the TODOs-list file"
[CHANGELOG]: ./CHANGELOG.md "View Sublime-Alan's CHANGELOG file"
[WORK_NOTES]: ./WORK_NOTES.md "View my working notes file"

<!--------- SCREENSHOTS --------->

[Screenshot Build Console]: ./screenshots/Build_Errors_Console.png "Screenshot of Sublime-Alan build system errors log in ST's console"
[Screenshot Build Editor]:  ./screenshots/Build_Errors_Editor.png "Screenshot of Sublime-Alan build system errors navigation (using 'Monokai' color scheme)"
[Screenshot Alan DarkFluo]:  ./screenshots/Alan_DarkFluo.png "Screenshot of 'Alan DarkFluo' color scheme"
