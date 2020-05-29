# Using ZeroMQ with Google Protocol Buffers

I wanted to figure out how to use ZeroMQ as the messaging platform and Google Protocol Buffers as the
serialization on top of ZeroMQ. This [StackOverflow thread](https://stackoverflow.com/questions/7390561/zeromq-protocol-buffers)
was extremely helpful.

I'm specifically using [cppzmq](https://github.com/zeromq/cppzmq), which seems to be the most popular C++ binding
for ZeroMQ right now. It's pretty nice so far although I've only built this trivial example by adapting some of the advice
from the StackOverflow thread.

It's also using CMake, building ZeroMQ from source and finding ProtoBuf on the system. The data type is serialized by converting
to a string and it's deserialized by parsing as an array.

The C++ binding for ZeroMQ handles converting the string to binary data.
