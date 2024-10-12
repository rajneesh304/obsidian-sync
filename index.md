```dataviewjs
const root = ""; // Set root folder if necessary

function renderFolder(folderPath, indentLevel) {
    const indent = " ".repeat(indentLevel * 4); // Adjust the indent spaces
    const folderPages = dv.pages(`"${folderPath}"`).where(p => p.file.path.startsWith(folderPath));
    const subfolders = [...new Set(folderPages.map(p => p.file.folder))].filter(f => f !== folderPath);

    // Display current folder name
    dv.paragraph(`${indent}- ${folderPath}`);

    // List all files in the current folder
    folderPages
        .where(p => p.file.folder === folderPath)
        .forEach(file => dv.paragraph(`${indent}  - ${file.file.name}`));

    // Recursively render subfolders
    subfolders.forEach(subfolder => {
        renderFolder(subfolder, indentLevel + 1);
    });
}

// Start rendering from the root folder
renderFolder(root, 0);

```


