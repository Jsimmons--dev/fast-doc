This function will find all freshDoc references in your markdown and figure out if the code
block has changed. This file does not handle updating the markdown.

This uses the core library to find all code blocks
```javascript @freshdoc ./getBlockChanges.mjs:16-16
//getBlockChanges.mjs:16-16
    const { codeBlocks } = await getItems()
```



### Giving Helpful output
Giving helpful output for the changes command is currently done at the end of this file.
```javascript @freshdoc ./getBlockChanges.mjs:76-84
//getBlockChanges.mjs:76-84
    if (filesWithErrors.length > 0) {
        console.log()
        console.log("FreshDoc️ found differences the Docs and the Code")
        for (const file of filesWithErrors) {
            console.log(file)
        }
        console.log()
        process.exit(0)
    }
```

output will be in the form freshdocReference - codeReference
```
markdownFile.md:3 - code.mjs:34
```

These names are gathered from 
```javascript @freshdoc ./getBlockChanges.mjs:64-74
//getBlockChanges.mjs:64-74
    const filesWithErrors = []
    for (const codeBlock of codeBlocks) {
        const { sourceMarkdown, referencedCodeFilename,
            codeBlockRangeStart, codeBlockRangeEnd, markdownFreshDocReferenceLineNumber,
        } = codeBlock
        const code = referenceMap[buildCodeReference(referencedCodeFilename, codeBlockRangeStart)]
        const markdown = referenceMap[buildMarkdownReference(sourceMarkdown, markdownFreshDocReferenceLineNumber)]
        if (!markdownAndCodeAreTheSame(markdown, code)) {
            filesWithErrors.push(`${sourceMarkdown}:${markdownFreshDocReferenceLineNumber} != ${referencedCodeFilename}:${codeBlockRangeStart}`)
        }
    }
```
