```dataviewjs
const root = ""; // Set root folder if necessary

function renderFolder(folderPath, indentLevel) {
    const folderPages = dv.pages(`"${folderPath}"`).where(p => p.file.path.startsWith(folderPath));
    const subfolders = [...new Set(folderPages.map(p => p.file.folder))].filter(f => f !== folderPath);

    // Create a list element for the folder
    const ul = dv.el('ul', null, { style: `margin-left: ${indentLevel * 20}px;` });

    // List all files in the current folder
    folderPages
        .where(p => p.file.folder === folderPath)
        .forEach(file => {
            const li = dv.el('li', `📄 [${file.file.name}](${file.file.path})`, ul);
        });

    // Recursively render subfolders
    subfolders.forEach(subfolder => {
        const li = dv.el('li', `📁 **${subfolder}**`, ul);
        renderFolder(subfolder, indentLevel + 1); // Recursive call for subfolders
    });
}

// Start rendering from the root folder
renderFolder(root, 0);

```
