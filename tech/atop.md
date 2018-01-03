# ATOP metrics

| Group         | Metric        | Description                                        |
| ------------- |:-------------:| --------------------------------------------------:|
| CPU           |               | Percentage of CPU time spent                       |
|               | sys           | in kernel mode                                     |
|               | user          | in user mode                                       |
|               | irq           | interrupt handling                                 |
|               | idle          | unused cpu time while no processes were waiting io |
|               | wait          | cpu time at least one process was waiting io       |
| CPL           |               | CPU load information (number of threads that available to run on cpu or waiting for io)|
|               | csw           | number of context switches       |
|               | intr          | number of interuptions       |