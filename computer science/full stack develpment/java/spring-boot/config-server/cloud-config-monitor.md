This is the best way to refresh the [[spring configuration]]. we need to set a [[webhook]] url in [[GitHub]], so if any changes in the github it will trigger our [[webhook]] url. and all the other things will taken care, if we configured appropriately.

This is used to refresh the [[spring configuration]] without any refresh and we don't even need to hit any endpoint like [[refresh]] and [[busrefresh]].

but it internally used [[spring cloud bus]], so we need to mention the dependency and the [[application.properties or application.yml]] configuration.

>ref: [[hookdeck]]