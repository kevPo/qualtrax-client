<template>
    <div>
        <h1>Docs</h1>
        <div class="label-input">
            <label>Number of Folders</label>
            <input type="number">
        </div>
        <div class="label-input">
            <label>Number of Documents Per Folder</label>
            <input type="number">
        </div>
        <div class="label-input">
            <label>Base Document Id</label>
            <input type="number">
        </div>

        <button @click="create">Create</button>
    </div>
</template>

<script>
export default {
    methods: {
        async create() {
            let createFolder = fetch(`https://localhost:44301/api/folders`, {
                method: "POST",
                headers: {
                    "User-Agent": "test",
                    "Content-Type": "application/json",
                    Accept: "application/vnd.qualtrax.v1+json",
                    Authorization: `Bearer F8992A00-27BB-4466-9D77-CA056DF06D62`
                },
                body: JSON.stringify({parentId: -1, title: "folder "})
            });
            
            const createFolderBodies = function(incrementer) {
                return {
                    method: "POST",
                    headers: {
                        "User-Agent": "test",
                        "Content-Type": "application/json",
                        Accept: "application/vnd.qualtrax.v1+json",
                        Authorization: `Bearer F8992A00-27BB-4466-9D77-CA056DF06D62`
                    },
                    body: JSON.stringify({parentId: -1, title: `Folder ${incrementer}`})
                };
            }

            let folderBodies = [];

            for (var i = 0; i < 1; i++) {
                folderBodies.push(createFolderBodies(i));
            }

            const createFolderUrl = "https://localhost:44301/api/folders";
            const folderResults = await Promise.all(folderBodies.map(body => fetch(createFolderUrl, body).then(r => r.json())));
            console.log(folderResults);

            const createDocumentBody = function(folderId) {
                const myDocument = {
                    parentId: folderId,
                    editorId: 1,
                    documentManagerId: 1,
                    isControlled: true,
                    generatePDF: false,
                    showInTree: true
                };

                const body = JSON.stringify({sourceDocumentId: 4, document: myDocument});
                
                return {
                    method: "POST",
                    headers: {
                        "User-Agent": "test",
                        "Content-Type": "application/json",
                        Accept: "application/vnd.qualtrax.v1+json",
                        Authorization: `Bearer F8992A00-27BB-4466-9D77-CA056DF06D62`
                    },
                    body: body
                };
            }
            
            let documentBodies = [];

            folderResults.forEach(folder => {
                for (var i = 0; i < 1; i++) {
                    documentBodies.push(createDocumentBody(folder.id));
                }
            });

            const createDocumentUrl = "https://localhost:44301/api/documents";
            const documentResults = await Promise.all(documentBodies.map(body => fetch(createDocumentUrl, body).then(r => r.json())));
            
            console.log(documentResults);
        }
    }
}
</script>