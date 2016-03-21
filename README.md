# spinnerQueue
jQuery widget for loading spinner.
Allows create queues of tasks during which loading spinner will be shown.

Example:
```HTML
    <!-- Include Required Prerequisites -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.11.4/jquery-ui.min.js"></script>

    <!-- spinnerQueue -->
    <script src="spinnerQueue/spinnerQueue.js" type="text/javascript"></script>
    <link  href="spinnerQueue/spinnerQueue.css" rel="stylesheet" type="text/css" />

    <script>
        $('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'}).spinnerQueue('started', 'pageLoad', false);
        $( document ).ready(function() {
            $('body').spinnerQueue().spinnerQueue('finished', 'pageLoad');
        });
    </script>
```

### Init
```JavaScript
$('body').spinnerQueue()
```
or
```JavaScript
$('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'})
```
### On task start
For first use, with initialization
```JavaScript
$('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'}).spinnerQueue('started', 'pageLoad');
```
Recommend using
```JavaScript
$('body').spinnerQueue().spinnerQueue('started', 'pageLoad'); // With initialization
// If spinnerQueue is already initialized, nothing will be changed
```
or
```JavaScript
$('body').spinnerQueue('started',  'pageLoad');
```

### On task finish
```JavaScript
$('body').spinnerQueue('finished', 'pageLoad');
```

### How to use your own animation
```CSS 
body .spinnerQueue {
    background-color: rgba(5,55,155, 0.2);
}

body .spinnerQueue .spinner-bg {
    height: 100px;
    width: 100px;
}

body .spinnerQueue .spinner-image {
    width: 100px;
    height: 100px;
    background-color: rgba(0,0,0,0);
    background: url('spinner.gif');    
    -webkit-animation: none;
    animation: none;
}
```

### Commands:
##### Started
```JavaScript
spinnerQueue('started', key, [isCumulative])
```

| Parameters | Description   |
|------------|---------------|
| **key**<br>(Type: String)   | Name of task. |
| **isCumulative**<br>(Type: Boolean, default: *False*) | If *isCumulative* equal *True* every next call *spinnerQueue('started', key, true)* or *spinnerQueue('started', key)* will increases number of using *key* task by 1.<br>In order to remove *key* task from queue spinnerQueue('finished', key) must be called appropriate number times.<br>If *isCumulative* equal *False* then one call spinnerQueue('finished', key) remove *key* task from queue. |

##### Finished
```JavaScript
spinnerQueue('finished', key)
```
| Parameters | Description   |
|------------|---------------|
| **key**<br>(Type: String)   | Name of task. |

##### Setup or update options:
```JavaScript
var options = {
    queue     : { 'task1':true, 'cumulativeTask':2 },
    showSpeed : 'fast', 
    hideSpeed : 'fast',
};
$('body').spinnerQueue(options);
```

**showSpeed**, **hideSpeed**
: Speed are given in milliseconds; higher values indicate slower animations, not faster ones. The strings 'fast' and 'slow' can be supplied to indicate durations of 200 and 600 milliseconds, respectively. If any other string is supplied, or if the duration parameter is omitted, the default duration of  400 milliseconds is used.

**queue**
: It is object that contains tasks names as keys.
: If value of key is *True* then one call of spinnerQueue('finished', key) is enough to removing task from queue. If spinnerQueue('started', key) or spinnerQueue('started', key, false) is already called, nothing will change.
: If value of key is *Number* then every spinnerQueue('started', key, [true]) increases value by 1. Task with name *key* deletes if spinnerQueue('finished', key) will be called *value* times

#### Destroy
Remove spinner from DOM
```JavaScript
$('body').spinnerQueue('destroy');
```
#### isInQueue
```JavaScript
var inQueue = $('body').spinnerQueue('isInQueue', key);
```
#### isInQueue
```JavaScript
var isEmpty = $('body').spinnerQueue('isQueueEmpty');
```
#### queueSize
```JavaScript
var size = $('body').spinnerQueue('queueSize');
```

