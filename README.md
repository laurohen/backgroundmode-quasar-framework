# backgroundmode-quasar-framework
Check App Background Status in Projects Using Quasar Framework


The plugin can be installed via Cordova-CLI and is publicly available on NPM.
Execute from the projects root folder:

$ cordova plugin add cordova-plugin-background-mode

first step is always to generate a new plugin using Quasar CLI:

$ quasar new boot <name>
Where <name> should be exchanged by a suitable name for your boot file.

This command creates a new file: /src/boot/<name>.js with the following content:
  
  
// "async" is optional
// store --- Use to store status value and reuse elsewhere in project
export default async ({ store }) => {  
  
 document.addEventListener('deviceready', () => {

  cordova.plugins.backgroundMode.enable();
  
// -------------- Quirks ------------
//Various APIs like playing media or tracking GPS position in background might not work while in background even the background mode is //active. To fix such issues the plugin provides a method to disable most optimizations done by Android/CrossWalk.

  cordova.plugins.backgroundMode.on('activate', () => {
    alert('App Background on');         
    store.commit('increment_screen');
        
  });
        
  cordova.plugins.backgroundMode.on('deactivate', () => {
    alert('App Background off');
    store.commit('increment_screen');

  });  
 
 
 
 
 } , false)
    
}
