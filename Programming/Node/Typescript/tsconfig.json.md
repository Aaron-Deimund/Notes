Stores compiler options
specifies included and excluded files
Supports configuration inheritance.
Can selectively override settings.

A simple typescript configuration:

```json
{
	"compilerOptions":{
		"target": "es5",
		"noUnusedLocals": true,
		"outFile": "output.js"
	},
	"files":[
		"app.ts"
	]
}
```
