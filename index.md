
```dataviewjs 
let pages = dv.pages().file.path;
let folderStructure = {};

pages.forEach(page => {
    let parts = page.split('/');
    let fileName = parts.pop();
    let currentFolder = folderStructure;

    parts.forEach(part => {
        if (!currentFolder[part]) {
            currentFolder[part] = {};
        }
        currentFolder = currentFolder[part];
    });

    if (!currentFolder['_files']) {
        currentFolder['_files'] = [];
    }
    currentFolder['_files'].push(page);
});

function renderFolderStructure(folder, indent = 0) {
    let indentSpace = ' '.repeat(indent * 4);
    for (let folderName in folder) {
        if (folderName === '_files') {
            folder[folderName].forEach(filePath => {
                let fileName = filePath.split('/').pop();
                dv.paragraph(`${indentSpace}- `).append(dv.fileLink(filePath, fileName));
            });
        } else {
            dv.header(3, `${indentSpace}${folderName}`);
            renderFolderStructure(folder[folderName], indent + 1);
        }
    }
}
renderFolderStructure(folderStructure);

```
