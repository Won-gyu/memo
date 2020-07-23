By Gaurav Pandvia

Browser Web APIs- threads created by browser implemented in C++ to handle async events like DOM events, http request, setTimeout, etc.

Event Loop now is responsible for the execution of these callbacks in the queue and pushing it in the stack, when it is empty.
Event loop basic job is to look both at the stack and the task queue, pushing the first thing on the queue to the stack when it see stack as empty.

![1](https://miro.medium.com/max/700/1*-MMBHKy_ZxCrouecRqvsBg.png)

[source](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)