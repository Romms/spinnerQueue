# spinnerQueue
jQuery widget for loading spinner

Example:
    <!-- Include Required Prerequisites -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.11.4/jquery-ui.min.js"></script>

    <!-- spinnerQueue -->
    <script type="text/javascript" src="spinnerQueue/spinnerQueue.js')}"></script>
    <link rel="stylesheet" type="text/css" href="spinnerQueue/spinnerQueue.css')}" />

    <script>
        $('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'}).spinnerQueue('started', 'pageLoad', false);
        $( document ).ready(function() {
            $('body').spinnerQueue().spinnerQueue('finished', 'pageLoad');
        });
    </script>

Init
---

$('body').spinnerQueue()
$('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'})

On event start 
---
$('body').spinnerQueue({showSpeed: 'fast', hideSpeed:'fast'}).spinnerQueue('started', 'pageLoad', false); // With initialization
or
$('body').spinnerQueue().spinnerQueue('started', 'pageLoad', false); // With initialization
or
$('body').spinnerQueue('started',  'pageLoad', false);


On event finish
---
$('body').spinnerQueue('finished', 'pageLoad', false);
