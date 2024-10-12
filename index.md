```dataviewjs
const root = "/"; // Set root folder if necessary

function renderFolder(folderPath, indentLevel) {
    const indent = " ".repeat(indentLevel * 2); // Adjust the indent for readability
    const folderPages = dv.pages(`"${folderPath}"`).where(p => p.file.path.startsWith(folderPath));
    const subfolders = [...new Set(folderPages.map(p => p.file.folder))].filter(f => f !== folderPath);

    // Display the folder name as a header
    dv.list([`${indent}- **${folderPath}**`]);

    // List all files in the current folder as links
    folderPages
        .where(p => p.file.folder === folderPath)
        .forEach(file => {
            dv.list([`${indent}  - [${file.file.name}](${file.file.path})`]); // Create clickable file links
        });

    // Recursively render subfolders
    subfolders.forEach(subfolder => {
        renderFolder(subfolder, indentLevel + 1);
    });
}

// Start rendering from the root folder
renderFolder(root, 0);

```


