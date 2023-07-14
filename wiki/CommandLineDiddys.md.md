JPS - https://docs.oracle.com/en/java/javase/17/docs/specs/man/jps.html

running java processes = jps -lV

#### Find java and remove applications you don’t want killed

```bash
jps | egrep -v (pgrep idea)
```

#### Find apps running jvm, deliminate by first space, return the field1 (PID), kill all -

```bash
for pid in $(jps | egrep -v $(pgrep webstorm) | egrep -v $(pgrep idea)| egrep -v $(pgrep jps) | cut -d' ' -f1); do kill -9 $pid; done
```