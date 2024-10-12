```dataviewjs
    const allFiles = dv.pages("")
    const targetFolder = "Tools"
    const depthLimit = 1
    
    const rootFolder = dv.app.vault.fileMap[targetFolder]
   
    const files = []
    
    while(file.length) {
      const [file, depth] = file.pop()
      files.push(file)
    
      if (file.children?.length && depth < depthLimit) {
        console.log("concat children!")
        fileStack = fileStack.concat(file.children.map(o => ([o, depth + 1])))
      }
      console.log("-----> recurse!", file, depth, fileStack)
    }
    
    console.log(files)
    files.forEach(file => dv.el("p", file.name))
```
