# a easy timeline manager
----

@version 1.4.1  
@author dron

## Basic usage:

```
// get a timeline instance. 
// as long as you are willing, you can create an unlimited number of Timeline instance.
// but we don't suggest you to do so.
var timeline = Timeline.use( timelineKey ).init( ms ); // ms defaults to 1e3/60
// create a task.
// you can create an unlimited number of task in the same timeline.
var task = timeline.createTask( {
  // start time, defaults to 0.
  start: ms,
  // duration of task, defaults to 0, if specify to -1, task will always run.
  duration: ms,
  // who all events call with.
  object: obj,
  // event listener, it will trigger when task start.
  onStart: fn, 
  // event listener, it ongoing trigger after the start. argument 't' values range from 0 to duration.
  onUpdate: function( t ){},
  // event listener, it will trigger when task end.
  onEnd: fn,
  // event listener, it will trigger when task stop.
  onStop: fn
} );
// stop a task, and trigger the 'stop' event.
task.stop();
Advanced Usage:
Timeline static functions:
// for stopping all timeline instances, it can be used for making the game pause.
Timeline.stopAllTimer();
// start all timeline instances.
Timeline.startAllTimer();
// stop all tasks of all timeline instances.
Timeline.clearAllTasks();
Timeline instance methods:
// stop all tasks of a timeline instance.
timeline.clearTasks();
// create a task for delayed callback, it simulated window.setTimeout.
timeline.setTimeout( fn, time );
// stop a task for delayed callback.
timeline.clearTimeout( timer );
```