# linux 信号量之SIGNAL 0

http://www.linuxjournal.com/content/monitoring-processes-kill-0

“signal 0″ is kind of like a moral equivalent of “ping”.

Using “kill -0 NNN” in a shell script is a good way to tell if PID “NNN” is alive or not:

signal 0 is just used to check process is exists or not.

```
#!/bin/bash

trap 'kill $(jobs -p)' EXIT

/opt/test/service &
PID=$!

/bin/systemd-notify --ready

while(true); do
    FAIL=0

    kill -0 $PID
    if [[ $? -ne 0 ]]; then FAIL=1; fi

#    curl http://localhost/test/
#    if [[ $? -ne 0 ]]; then FAIL=1; fi

    if [[ $FAIL -eq 0 ]]; then /bin/systemd-notify WATCHDOG=1; fi

    sleep 1
done

```

# 使用kill -l查看所有的信号量
