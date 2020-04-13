Web audio API is an audio api that allows you to do coool shit like make synthesizers, trigger audio, ect...

```
var audioCtx = new(window.AudioContext || window.webkitAudioContext)();

var oscillator = audioCtx.createOscillator();
oscillator.connect(audioCtx.destiintion)
```