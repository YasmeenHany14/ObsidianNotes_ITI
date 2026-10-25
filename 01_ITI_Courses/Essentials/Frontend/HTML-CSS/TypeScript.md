---
notion-id: 12eba0f393fd8099b6a3d937f95f9210
---
### Using ts compiler on the fly:
```bash
npx --package typescript tsc --help
tsc: compiler name
to specify compliation path:
npx --package typescript tsc --outDir dist file.ts
```
  
### Installing and configuring ts compiler for projects
```bash
1- add package.json
	npm init -y
2- install ts
	npm install typescript --save-dev
	* next edit the script line inside the package.json file to the following
		  "scripts": {
			    "tsc": "tsc"
			 },
3- get the tsconfig.json
npm run tsc -- --init
4- uncomment the following configs:
	1- "sourceMap": true,  
	2- "outDir": "./dist",    
	3- "moduleResolution": "node10",   
	4- "target": "es2017", 
	
5- now to run write in terminal
	npm run tsc
```
  
### TS Types:
1. string
2. number (works for decimal, floats, any type of number)
3. boolean
4. array (works for custom datatypes too)
5. null
6. undefined
7. any (any type can be assigned here) (not encouraged to use)
8. void (for functions)
9. Enum (set of named constants) (enums minimize “magic strings” in code
`variableName: type`
Assigning many types: `let firstName = string | undefined | null`
  
```jsx
let firstName = 'Dan' // typeinference (no need to explicitly specfiying datatype)
let firstBtats;
firstBtats = 'SS'; // type is any now
let firstBtats2: string;
let productNames = ['btats', 'btats', 'btats'];
let productNames2: string[] = []; //string array if not specified will be any
// assinging null to a string
firstBtats2 = null // error because string cannot be assigned null  
                   // This error depeneds on the ts config, if strict mode is on
                   
// Enums
enum sports {
    btats,
    btats1, 
    btats2
} // watch js complied code, enums are converted to functions
let btats = sports.btats; // assign literal string value in js code
const enum sports2 {
    btats,
    btats1, 
    btats2
} // no js compiled here when const
let btats2 = sports2.btats2; // assign enum string number in the js code
```
  
### TS Functions
  
// LOOK UP destructuring PARAMETERS (counter argument is it is less readable)