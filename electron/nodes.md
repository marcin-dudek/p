# quick start explanation

# open dev tools

# improvements
  mainWindow.once('ready-to-show', () => {
    mainWindow.show()
  })


# headless
 // html
var { ipcRenderer } = require('electron');

document.getElementById('btn1').addEventListener('click', function () {
    ipcRenderer.send('shutdown', { msg: 'window' })
})

//main.js
ipc.on('shutdown', function (e) {
  app.quit()
})