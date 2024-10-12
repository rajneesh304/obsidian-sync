
```dataviewjs
function renderFolder(folderPath, indentLevel) {
    const folder = dv.pages(`#${folderPath}`).filter(p => p.file.path.startsWith(folderPath));
    const subfolders = [...new Set(folder.map(p => p.file.folder))];
    
    subfolders.forEach(subfolder => {
        const indent = " ".repeat(indentLevel * 2);
        dv.span(`${indent}- **${subfolder}**`);
        dv.el("br");
        
        const files = folder.filter(p => p.file.folder === subfolder);
        files.forEach(file => {
            const fileIndent = " ".repeat((indentLevel + 1) * 2);
            dv.span(`${fileIndent}- ${file.file.name}`);
            dv.el("br");
        });
        
        renderFolder(subfolder, indentLevel + 1);
    });
}

renderFolder("/", 0);

```



[[avc|RAG]]

