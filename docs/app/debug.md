# tools

## rr

rr aspires to be your primary C/C++ debugging tool for Linux, replacing — well, enhancing — gdb. You record a failure once, then debug the recording, deterministically, as many times as you want. The same execution is replayed every time.

Start by using rr to record your application:

$ rr record /your/application --args
...
FAIL: oh no!

The entire execution, including the failure, was saved to disk. That recording can now be debugged.

$ rr replay
GNU gdb (GDB) ...
...
0x4cee2050 in _start () from /lib/ld-linux.so.2
(gdb)

Remember, you're debugging the recorded trace deterministically; not a live, nondeterministic execution. The replayed execution's address spaces, register contents, syscall data etc are exactly the same in every run.

Most of the common gdb commands can be used.

(gdb) break mozilla::dom::HTMLMediaElement::HTMLMediaElement
...
(gdb) continue
Continuing.
...
Breakpoint 1, mozilla::dom::HTMLMediaElement::HTMLMediaElement (this=0x61362f70, aNodeInfo=...)
...

If you need to restart the debugging session, for example because you missed breaking on some critical execution point, no problem. Just use gdb's run command to restart replay.

(gdb) run
The program being debugged has been started already.
Start it from the beginning? (y or n) y
...
Breakpoint 1, mozilla::dom::HTMLMediaElement::HTMLMediaElement (this=0x61362f70, aNodeInfo=...)
...
(gdb)

The run command started another replay run of your recording from the beginning. But after the session restarted, the same execution was replayed again. And all your debugging state was preserved across the restart.

Note that the this pointer of the dynamically-allocated object was the same in both replay sessions. Memory allocations are exactly the same in each replay, meaning you can hard-code addresses you want to watch.

Even more powerful is reverse execution. Suppose we're debugging Firefox layout:

Breakpoint 1, nsCanvasFrame::BuildDisplayList (this=0x2aaadd7dbeb0, aBuilder=0x7fffffffaaa0, aDirtyRect=..., aLists=...)
   at /home/roc/mozilla-inbound/layout/generic/nsCanvasFrame.cpp:460
460   if (GetPrevInFlow()) {
(gdp) p mRect.width
12000

We happen to know that that value is wrong. We want to find out where it was set. rr makes that quick and easy.

(gdb) watch -l mRect.width
(gdb) reverse-cont
Continuing.
Hardware watchpoint 2: -location mRect.width
Old value = 12000
New value = 11220
0x00002aaab100c0fd in nsIFrame::SetRect (this=0x2aaadd7dbeb0, aRect=...)
   at /home/roc/mozilla-inbound/layout/base/../generic/nsIFrame.h:718
718       mRect = aRect;

This combination of hardware data watchpoints with reverse execution is extremely powerful!

https://rr-project.org/
