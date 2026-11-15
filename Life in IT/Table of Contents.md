```dataviewjs
const excluded = new Set(["Table of Contents"]);
const root = { folders: new Map(), files: [] };

// Include Markdown and image files
const extensions = ["md", "jpg", "jpeg", "png"];

const files = app.vault.getFiles()
    .filter(file => extensions.includes(file.extension.toLowerCase()))
    .filter(file => !excluded.has(file.basename));

for (const file of files) {
    const parts = file.path.split("/");
    parts.pop();

    let current = root;

    for (const folder of parts) {
        if (!current.folders.has(folder)) {
            current.folders.set(folder, {
                folders: new Map(),
                files: []
            });
        }

        current = current.folders.get(folder);
    }

    current.files.push(file);
}

function renderTree(node, depth = 0) {
    const container = document.createElement("div");

    container.style.paddingLeft = depth === 0 ? "0px" : "24px";

    const folders = [...node.folders.entries()]
        .sort((a, b) =>
            a[0].localeCompare(b[0], undefined, {
                numeric: true
            })
        );

    for (const [name, child] of folders) {
        const details = document.createElement("details");

        // Collapsed by default
        const summary = document.createElement("summary");
        summary.textContent = "📁 " + name;
        summary.style.cursor = "pointer";

        details.appendChild(summary);
        details.appendChild(renderTree(child, depth + 1));

        container.appendChild(details);
    }

    const sortedFiles = node.files.sort((a, b) =>
        a.basename.localeCompare(b.basename, undefined, {
            numeric: true
        })
    );

    for (const file of sortedFiles) {
        const line = document.createElement("div");

        line.style.paddingLeft = "24px";
        line.style.margin = "4px 0";

        const link = document.createElement("a");
        link.className = "internal-link";
        link.href = file.path;
        link.dataset.href = file.path;

        const icon = file.extension === "md" ? "📄 " : "🖼️ ";
        link.textContent = icon + file.name;

        line.appendChild(link);
        container.appendChild(line);
    }

    return container;
}

dv.container.appendChild(renderTree(root));
```
