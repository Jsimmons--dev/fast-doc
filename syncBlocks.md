This function deals with syncing changes in your fast doc code blocks.


In order to rewrite markdown files and insert the code blocks properly, we need to take into account
which code blocks previously had contents, and when we remove it, how to offset by that amount of lines.
``` javascript @freshdoc ./syncBlocks.mjs:31-39
            let numberOfDeletedLines = 0
            for (let i = markdownFreshDocReferenceLineNumber; i < markdownLines.length; i++) {
                if (endOfCodeBlockRegex.test(markdownLines[i])) {
                    endOfMarkdownCodeBlock = i
                    break
                } else {
                    numberOfDeletedLines++
                }
            }
```