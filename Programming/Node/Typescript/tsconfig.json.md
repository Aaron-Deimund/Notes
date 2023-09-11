# Configuration

## tsconfig.json
* Stores compiler options
* specifies included and excluded files
* Supports configuration inheritance.
* Inherited configs can selectively override settings.

## A simple typescript configuration:

```json
{
  "compilerOptions": {
    "target": "es2016",                      
	"sourceMap": true,
    "outDir": "js", 
    "noEmit": false,  
    "forceConsistentCasingInFileNames": true,
    "strict": true
  },
  "files":[
    "app/app.ts"
  ]
}
```

create file 
```
tsc --init
```
