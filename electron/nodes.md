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

# global shortcut
const {app, globalShortcut} = require('electron')

app.on('ready', () => {
  // Register a 'CommandOrControl+X' shortcut listener.
  const ret = globalShortcut.register('CommandOrControl+X', () => {
    console.log('CommandOrControl+X is pressed')
  })

  if (!ret) {
    console.log('registration failed')
  }

  // Check whether a shortcut is registered.
  console.log(globalShortcut.isRegistered('CommandOrControl+X'))
})

app.on('will-quit', () => {
  // Unregister a shortcut.
  globalShortcut.unregister('CommandOrControl+X')

  // Unregister all shortcuts.
  globalShortcut.unregisterAll()
})
