= node-lwes 

LWES - Light Weight Event System library for nodejs. Currently we only support listening to events but plan to support emmitting events as well.

* http://www.lwes.org
* http://sourceforge.net/projects/lwes

== Installation

=== Installing npm (node package manager)
  curl http://npmjs.org/install.sh | sh

=== Installing lwes 
  [sudo] npm install lwes

== Usage (see examples/lwes_listener.js for full example)

  var LWES = require('lwes').LWES;
  var lwesObj = new LWES();
  var filteredEvents = ['EventTypeA', 'EventTypeB']

  lwesObj.createListener(filteredEvents, function(lwesEvent) {
    console.log("I Found a filtered event: " + lwesEvent.type);
  });

== Contributing to node-lwes 
 
* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.

== Copyright

Copyright (c) 2011 Aaron Qian. See LICENSE.txt for
further details.

