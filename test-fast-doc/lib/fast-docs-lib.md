
This method uses the vfile-find-down package to go and get every Markdown file in the project.
You need to use findDownAll and not findDown, otherwise you only get the first result.

``` javascript @fastdoc ./fast-docs-lib.mjs:21-26
async function getFastDocItems() {
    const markdowns = await findDownAll('.md')

    const fastDocLinks = []
    const fastDocCodeBlocks = []
    for (const file of markdowns) {
```

This method will then take every link it can find in the file and strip it out and return it.

For our v1, any link that we found we are considering a fastDoc Link.

The big gnarly regex at the top of the file is what finds those links.

More explanation on that regex to come...