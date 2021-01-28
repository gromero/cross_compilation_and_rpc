On host:

```
gromero@gromero0:~/git/cross_compilation_and_rpc$ uname -a 
Linux gromero0 5.4.0-62-generic #70-Ubuntu SMP Tue Jan 12 12:45:47 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
gromero@gromero0:~/git/cross_compilation_and_rpc$ python3 cross_compilation_and_rpc.py 
Generating .so: arm-linux-gnueabihf-g++-9 -shared -fPIC -o ./lib.so /tmp/tmpnnly184x/lib0.o
1.21198e-05 secs/op
```

On remote device (target). In that example the target is a RPI 3, no g++ installed:
```
gromero@raspberrypi:~/git/tvm $ uname -a 
Linux raspberrypi 5.4.81-v7+ #2 SMP Sat Dec 12 20:10:08 -03 2020 armv7l GNU/Linux
gromero@raspberrypi:~/git/tvm $ g++
-bash: /usr/bin/g++: No such file or directory
gromero@raspberrypi:~/git/tvm $ python3 -m tvm.exec.rpc_server --host 0.0.0.0 --port=9090
INFO:root:If you are running ROCM/Metal, fork will cause compiler internal error. Try to launch with arg ```--no-fork```
INFO:RPCServer:bind to 0.0.0.0:9090
INFO:RPCServer:connection from ('192.168.2.108', 41938)
INFO:RPCServer:load_module /tmp/tmpj_apygug/lib.so
INFO:RPCServer:Finish serving ('192.168.2.108', 41938)
```
