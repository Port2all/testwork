# testwork
Single page application for viewing DropBox folders & files using dropbox API.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Technologies, used in app:
JS, Vue.js, Vue-router, Bootstrap, Bootstrap-Vue, Dropbox API, CSS, html.

### Vue files:

App.vue - for rendering header and router-view.

Home.vue - for connecting to dropbox (using API) and rendering dropboxViewer component.

dropboxViewer.vue - for showing current location, table heading, back button, empty-folder-error info and rendering File and/or Folder components.

File.vue - for showing files with their info (type, name, size, modification date) and checkbox for files-selection.

Folder.vue - for showing folders with their info (type and name)

router.js - for routing settings.


### JS-functions:
getFolderFromPath(path) - for recieving folder from dropbox.

back() - for going up through the folders.

formatBytes(size) - for smart-viewing of file-sizes.

formatDate(date) - for smart-viewing of last modified date (for files).

onFileClick() - for selecting files.

onFolderClick() - for folders opening.

onTrClick() - shows delete button for files.

onDeleteClick() -  shows alert with "Not implemented" massage for delete button.
