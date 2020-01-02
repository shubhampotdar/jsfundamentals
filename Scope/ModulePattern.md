# Modules
Modules encapsulate data and behavior (methods) together. The state (data) of a module is held by its methods via closure.
</br></br>
### Classic/Revealing Module Pattern
Javascript does not have the typical 'private' and 'public' specifiers. However, you can achieve the same effect through the clever application of Javascript's function-level scoping. The Revealing Module pattern is a design pattern for Javascript applications that elegantly solves this problem. The central principle of the Revealing Module pattern is that all functionality and variables should be hidden unless deliberately exposed. The best way to avoid exposing your top-level function to the global scope is to wrap everything in an IFFE. 
```javascript
// Classic/Revealing module pattern
var workshop = (function Module(teacher) {
  var publicAPI = { ask };
  return publicAPI;
  // ***************

  function ask(question) {
    console.log(teacher, question);
  }
})("Shu");

workshop.ask("Helllooooo"); // Shu Helllooooo
```

```javascript
var musicPlayer = function () {
  // Let's make sure no one can directly access our songList
  var songList = ['California Girls', 'California Dreaming', 'Hotel California'];  

  // We'll expose all these functions to the user
  function play () {
    console.log('Im playing the next song!');
  }

  function pause () {
    console.log('Im paused!');
  }

  function addTrackToMusicQueue (track) {
    songList.push(track);
    console.log('I added a song');
  }

  function showNextTrack () {
    console.log('My next track is', songList[0]);
  }

  // Let's hide this function
  function loadSong() {
    filesystem.loadNextSong();
  }

  return {
    playMusic: play,
    pauseMusic: pause,
    showNextTrack: showNextTrack,
    addTrack: addTrackToMusicQueue
  }
}

const musicModule = musicPlayer(); // invoke our musicPlayer to return it's object (module)
musicModule.playMusic(); // 'Im playing the next song!'
musicModule.pauseMusic(); // 'I'm paused!'
musicModule.showNextTrack(); // 'The next track is California Girls'

// Things we can't access...
musicModule.loadSong(); // error: not a function
musicModule.songList.push('White Rabbit'); // undefined error
```
</br></br>

### Module Factory

```javascript
//Module Factory 
function WorkshopModule(teacher) {
  var publicAPI = { ask, };
  return publicAPI;

  //******* 
  function ask(question) {
    console.log(teacher,question);
  }
};

var ws = WorkshopModule("Shu");
ws.ask("Module?"); // Shu Module?
```
</br></br>
### ES6 module pattern

#### workshop.mjs
```javascript
var teacher = "Shu";

export default function ask(question) {
  console.log(teacher,question);
};
```

#### Importing a module
* Named import syntax:
```javascript
import ask from "workshop.mjs";

ask("Default import");
```
* Namespace import syntax:
```javascript
import * as workshop from "workshop.mjs";

workshop.ask("Namespace import");
```



 
