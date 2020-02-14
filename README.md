# -vscode-js-definition-bug
Minimum reproducible example for VSCode bug

VSCode module imports in a Typescript project respect the tsconfig.json file. 
There is strange behaviour around setting `allowJS: false` within the tsconfig.json file.

Specifically, when attempting to cmd + click, Go to definition, or peek an imported file, certain filetypes do not work as expected.

It is my expectation, that VSCode should be unopinionated about the file types, and should still locate the file successfully, regardless of this config option. 

The following are the manual test results from importing different file types (.ts, .tsx, .js, .jsx) into every other file type.
For these tests, both relative and aliased imports were tested. 
Pass represents that cmd + click successfully directed to the file.
Fail represents that cmd + click did not go to the file, and would instead stay on the currently opened file.

## JS

### Aliased

- JS to TS aliased import - Fails
- JS to TSX aliased import - Fails
- JS to JS aliased import - Fails
- JS to JSX aliased import - Fails

### Relative

- JS to TS relative import - Passes
- JS to TSX relative import - Passes
- JS to JS relative import - Passes
- JS to JSX relative import - Passes

## JSX

### Aliased

- JSX to TS aliased import - Fails
- JSX to TSX aliased import - Fails
- JSX to JS aliased import - Fails
- JSX to JSX aliased import - Fails

### Relative

- JSX to TS relative import - Passes
- JSX to TSX relative import - Passes
- JSX to JS relative import - Passes
- JSX to JSX relative import - Passes

## TS

### Aliased

- TS to TS aliased import - Passes
- TS to TSX aliased import - Passes
- TS to JS aliased import - Fails
- TS to JSX aliased import - Fails

### Relative

- TS to TS relative import - Passes
- TS to TSX relative import - Passes
- TS to JS relative import - Fails
- TS to JSX relative import - Fails

## TSX

### Aliased 

- TSX to TS aliased import - Passes
- TSX to TSX aliased import - Passes
- TSX to JS aliased import - Fails
- TSX to JSX aliased import - Fails

### Relative

- TSX to TS relative import - Passes
- TSX to TSX relative import - Passes
- TSX to JS relative import - Fails
- TSX to JSX relative import - Fails
