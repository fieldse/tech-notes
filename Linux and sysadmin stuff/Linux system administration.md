

### Generate self-signed SSL certficates

from https://stackoverflow.com/questions/10175812/how-to-generate-a-self-signed-ssl-certificate-using-openssl

```shell
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365
```


### Show process listening on port

```shell
lsof -i :8000
```

### Monitor resource usage of a single process


```shell
 top -pid 41186
PID    COMMAND      %CPU TIME     #TH  #WQ  #POR MEM  PURG CMPR
41186  Python       0.0  00:00.34 2    0    19   10M  0B   0B
```

### Wait for a process to complete and get return code

```shell
wait ${PID}
```


### Show information about a process

from https://will-keleher.com/posts/What-can-you-do-with-a-pid.html

`ps -f $PID` gives an amazing high-level overview of what a process is doing. Being able to see the PID of the parent, uptime, and the actual command that's being run can really help debugging work.

```shell
> ps -f 41186
UID   PID  PPID   C STIME   TTY           TIME CMD
501 41186 35891   0 12:33PM ttys001    0:00.16 /usr/local/Cellar/python@3.10/3.10.6_1/Frameworks/Python.framework/Versions/3.10/Resources/Python.app/Contents/MacOS/Python -m http.server
```

-   `PPID`: the PID of the parent. If you're trying to understand why a process started, running `ps -f` on the PPID can give you some good clues!
-   `UID`: the user who started the process. `id -nu 501` will give you the username of the user who started the process.
-   `CMD`: the full command that's running!
-   `TTY`: the location of the TTY. As far as I know, there's no easy way to tail the TTY. Injecting output into it works though! `echo "hello tty" > /dev/ttys001` will make "hello tty" show up in the terminal that ran the initial command.


### Show sockets, ports, pipes, and network devices used by a process

from https://will-keleher.com/posts/What-can-you-do-with-a-pid.html

`lsof -p $PID -P`

```shell
> lsof -p $PID -P
COMMAND   PID USER   FD    TYPE            DEVICE SIZE/OFF                NODE NAME
Python  41186 will  cwd     DIR               1,4      192            51860960 /Users/will/tmp
Python  41186 will  txt     REG               1,4    49400            78478046 /usr/local/Cellar/python@3.10/3.10.6_1/Frameworks/Python.framework/Versions/3.10/Resources/Python.app/Contents/MacOS/Python
# ...omitting a long list of text files
Python  41186 will  txt     REG               1,4  2177216 1152921500312782996 /usr/lib/dyld
Python  41186 will    0u    CHR              16,1  0t12464                1095 /dev/ttys001
Python  41186 will    1u    CHR              16,1  0t12464                1095 /dev/ttys001
Python  41186 will    2u    CHR              16,1  0t12464                1095 /dev/ttys001
Python  41186 will    3u  systm 0x60e5bd939a75061      0t0                     [ctl com.apple.netsrc id 6 unit 50]
Python  41186 will    4u   IPv6 0x60e5bd936095681      0t0                 TCP *:8000 (LISTEN)
Python  41186 will    6u   unix 0x60e5bde017a4a71      0t0                     
```
