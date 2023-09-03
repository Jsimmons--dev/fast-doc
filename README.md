``` javascript @fastdoc ./main.mjs:5-5
program.name("freshDocs")
```


``` javascript @fastdoc ./main.mjs:7-12
program
  .command('sync' )
  .description('Sync all blocks')
  .action(() => {
    syncAllBlocks()
  })
```

``` javascript @fastdoc ./main.mjs:14-19
program
  .command('changes')
  .description('Get all changes')
  .action(() => {
    getAllChanges()
  })
```