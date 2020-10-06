
<p align="center">
  <img alt="githubdark-logo" src="https://cdn.jsdelivr.net/gh/StylishThemes/logos@master/github.dark/githubdark-mini.svg" width="580">
</p>
<h1 align="center"><b>Syntax Themes</b></h1>
<h2 align="center">Your eyes will&nbsp;:heart:&nbsp;you.</h2>

## Introduction

This will house the redesigned GitHub Dark syntax themes into a simpler theme switcher.

Everything in themes directory will need cleaning up and preparing, eventually!

## Do NOT install this theme, its not ready for any type of consumption.

## Benefits of this method

Currently if we have 10 syntax themes we need separate stylesheest for each scheme, then we need GitHub/Jupyter/CodeMirror sheets thats is already 30 stylesheets,
duplication of selectors alone is HUGE. This will cut that to a saner total.

Adding new color themes will be simpler, since they will follow an established preset,
this will cut implementation time of any theme by 2 thirds at least.

No more implementing only Github themes with missing counterparts.
this will be utterly disalowed by design. Anyone implementing a new theme has to complete all entries, test and ensure maximum bug free and consistency.

## Design methodology

There will be a userCSS select dropdown for the predefined themes + custom user selectable custom colors.

The new themes will be predefined just :root` color values, each `:root` color value will be assigned to the relevant selectors within the CodeMirror, Jupyter, GitHub, etc couterparts.

The theme switcher will then allow you to select one theme scheme and all 3 or 4 theme sheets will immediatly use the selected theme colors thoughout.

Users will not be able to select individual themes for Jupyter or CodeMirror/GitHub.

Example 

```css
@name         GitHub Dark Syntax Themes
@version      0.0.0
@description  A Syntax theme switcher for GitHub Dark
@namespace    StylishThemes
@author       StylishThemes
@homepageURL  https://github.com/StylishThemes/GitHub-Dark-Syntax-Themes
@supportURL   https://github.com/StylishThemes/GitHub-Dark-Syntax-Themes/issues/new/choose
@updateURL    https://github.com/StylishThemes/GitHub-Dark-Syntax-Themes/github-dark-syntax-themes.css
@license      BSD-2-Clause
@preprocessor stylus

@var select syntaxTheme "Choose syntax theme" [
	"Ambiance",
	"Twilight",
	"Custom"
]

@var color color-01 "Color 1"  #00f
@var color color-02 "Color 2"  #24c2c7
@var color color-03 "Color 3"  #cda869
@var color color-04 "Color 4"  #cf7ea9
@var color color-05 "Color 5"  #78cf8a
@var color color-06 "Color 6"  #aac6e3
@var color color-07 "Color 7"  #ffb795
@var color color-08 "Color 8"  #eed1b3

==/UserStyle== */

@-moz-document regexp("^https?://((education|gist|guides|docs|lab|raw|resources|status|developer|support)\\.)?github\\.com/((?!generated_pages/preview).)*$"), domain("githubusercontent.com"), domain("graphql-explorer.githubapp.com"), domain("www.githubstatus.com") {
  :root {
    if syntaxTheme=="Ambiance" {
      --color-01: #cf7ea9;
      --color-02: #9b859d;
      --color-03: #24c2c7;
      --color-04: #99c;
      --color-05: #555;
      --color-06: #aac6e3;
      --color-07: #af2018;
      --color-08: #00f;
    }
    else if syntaxTheme=="Twilight" {
      --color-01: #fc0;
      --color-02: #d6bb6d;
      --color-03: #cda869;
      --color-04: #777;
      --color-05: #8da6ce;
      --color-06: #f00;
      --color-07: #ff6400;
      --color-08: #aeaeae;
    }
    else if syntaxTheme=="Custom" {
      --color-01: color-01;
      --color-02: color-02;
      --color-03: color-03;
      --color-04: color-04;
      --color-05: color-05;
      --color-06: color-06;
      --color-07: color-07;
      --color-08: color-08;
    }
  }
  /* Codemirror */
  .cm-atom {
    color: var(--color-01) !important;
  }
  /* GitHub */
  .pl-c /* comment, punctuation.definition.comment, string.comment */ {
    color: var(--color-01)
  }
  /* Jupyter */
  #notebook .input_area:not(.highlight), body.api pre,
  :is(#notebook, body.api) .highlight,
  :is(#notebook, body.api) .highlight pre,
  :is(#notebook, body.api) .highlight table { background: var(--color-08) !important; color: var(--color-01) !important; }
}
```

## Todo

Some items in this todo list can be automated, if you know enough javaScript, please do help out, elase its all manual and tedious, and OMG.

Ideally each template will include all selectors in use, this is not true in some cases,
each OLD implementation we are basing this on within themes dir was pretty much dealers choice and followed no common standard.

Therefore the themes need cleaning up and asserting templates after some cleanup/pre work.

- [ ] Alphabetize all selectors in all themes Codemirror, GitHub, Jupyter
      (this will allow some sane order to extract the colors so that later these colors can be assigned in a way that works with the new design.)
- [ ] Extract colors
      Consider limiting each pallete to a fixed number of colors, currently some codemirror has 35 unique colors, there are 35 CSS vars then, too many IMO,
      Not all themes have 35 colors even, so K.I.S.S.
- [ ] These extracted colors need to be grouped greys with greys, greens with greens, reds with reds etch and so on, I think =)
- [ ] Assign extracted colors to the CSS vars
- [ ] Assign CSS vars in a manner that it works as close as possible to the actual themes (twilight will look like twilight, jupyter will look like jupyter etc).
- [ ] Implement `hljs` stylesheet, used in Github doc sites and graphql.
- [ ] Include missing diff colors and other syntax related selectors in respective themes so all colors match including diff colors etc.
- [ ] Add selectors for each theme is releavant part
- [ ] Ship it.

Something else I forget Im sure at this time, this is to get ball rolling.

## I want to help.

By all means, this is an insane undertaking, boring tedious work, we should coordinate so each person is doing one job no one else is doing, feel free to open an issue to discuss this.

ATM this job was self assigned, why IDK, but it needs doing, our syntax themes are insanely broken.

## Considerations

Uptream bugs in syntax themes need to be addressed also, see https://github.com/StylishThemes/GitHub-Dark/issues/1052
