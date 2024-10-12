```dataviewjs 
let title = "File Hierarchy"; let dir = "Your/Folder/Path"; // Replace with your folder path 
let processed = []; function listRecursive(folder, depth) {     
let files = [];    
let pages = dv.pages('"' + folder + '"');     
let currentFiles = "";     
pages.forEach(page => {        
if (page.file.folder === folder) {            
	currentFiles += page.file.link + " | ";        } 
else {            
	let nestedFolder = page.file.folder;            
	let isChild = folder.split('/').length + 1 === nestedFolder.split('/').length;             
		if (!processed.includes(nestedFolder) && isChild) {processed.push(nestedFolder);                files.push(listRecursive(nestedFolder, depth + 1));            }        }    });     if (currentFiles.endsWith(" | ")) {        currentFiles = currentFiles.slice(0, -3);    }     if (currentFiles !== "") files.unshift(currentFiles);         let path = folder.split('/').pop();    if (depth === 0) path = path;     files.unshift("<h3>" + path + "</h3>");    return files; } let files = listRecursive(dir, 0); dv.header(3, title); dv.list(files);
