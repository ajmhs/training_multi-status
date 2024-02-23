# Console application based on Shapes which displays use of Listeners on DataReaders and DataWriters

Skeleton created via
 
```bash
rtiddsgen -language C++11 -platform x64Linux4gcc7.3.0 -example x64Linux4gcc7.3.0 -create makefiles -create typefiles -d c++11 shapes.idl
```
The publisher creates three topics, called Topic1, Topic2, and Topic3, and creates DataWriters for each. It then writes basic shape to each topic in turn, using a different colour for each topic to allow for easier differentiation
on the reader side.

The subscriber creates three DataReaders, one for each topic. For the first reader, a read_condition is asigned and a waitset created. For the second reader a Listener is assigned, and the third reader is polled inside the main subscriber loop. Each of the handlers call a function which is guarded by a mutex, safely incrementing the global sample counter and writing output which differs by a prefix indicating the source: w = waitset, l = listener and p = polled. If the sample count parameter is used, it is multiplied by three to handle the three topics.
