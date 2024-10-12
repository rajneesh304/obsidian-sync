```dataviewjs
let pages = dv.pages().file.path;
let folderStructure = {};

// Building the folder structure
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

// Rendering the folder structure
function renderFolderStructure(folder, indent = 0) {
    let indentSpace = ' '.repeat(indent * 4);
    for (let folderName in folder) {
        if (folderName === '_files') {
            folder[folderName].forEach(filePath => {
                let fileName = filePath.split('/').pop();
                dv.span(`${indentSpace}- `).append(`[[${filePath}|${fileName}]]`);
                
            });
        } else {
            dv.span(`${indentSpace}**${folderName}**`);
            
            renderFolderStructure(folder[folderName], indent + 1);
        }
    }
}

// Call the rendering function
renderFolderStructure(folderStructure);

```



[[avc|RAG]]

