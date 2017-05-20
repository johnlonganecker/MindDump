### Do math on command line
**bc**

http://www.basicallytech.com/blog/archive/23/command-line-calculations-using-bc/

```
echo “obase=2;240” | bc
> 11110000
```
**chpst**

run a process as another user

```
chpst -u user:group command
```

**netstat**

```
netstat -nr
```

### I/O Redirection

```
dig - DNS lookup library
```

>

>>

### get requests on a port

** useful for see the exact value of a http header request**

```
netcat -l <port>
```

### base64 encoding

```
echo -n "admin:admin" | openssl base64
```

### base64 decoding

```
echo -n "YWRtaW46YWRtaW4=" | base64 --decode
```


** additional content **
http://www.tldp.org/LDP/abs/html/io-redirection.html

### telnet

**HTTP Request**

```bash
telnet www.google.com 80
```

Trying 216.58.217.132...
Connected to www.google.com.
Escape character is '^]'.
```
GET / HTTP/1.1


```
<output>

### wget

** Download files slower so roommates don't get mad **

```
wget --limit-rate=200k <file-name>
```

### tail

* tail process stdout *
tail -f /proc/<pid>/fd/1

### strace

* monitor interaction between kernel and process *
strace -e trace=open -p <pid> -s 80

### nmap

* scan these ports *
nmap -p25000-2000,8080,44

### openssl
https://jamielinux.com/docs/openssl-certificate-authority/create-the-root-pair.html
https://www.feistyduck.com/library/openssl-cookbook/online/ch-openssl.html#

* see all information *
openssl s_client -connect www.google.com:443

use s_client telnet with ssl

openssl x509 -in <file> -noout -text | less
openssl x509 -in <file> -text

* check to see if tls 1.0 is supported *
openssl s_client -connect rabbitmq-sb.svc.asv.ice.gecis.io:5671 -ssl3

* check to see if tls 1.0 is supported *
openssl s_client -connect rabbitmq-sb.svc.asv.ice.gecis.io:5671 -tls1`

* check to see if tls 1.1 is supported *
openssl s_client -connect rabbitmq-sb.svc.asv.ice.gecis.io:5671 -tls1_1

* check to see if tls 1.2 is supported *
openssl s_client -connect rabbitmq-sb.svc.asv.ice.gecis.io:5671 -tls1_2

* renewing certificate
openssl x509 -x509toreq -in fd.crt -out fd.csr -signkey fd.key

if no certificate is returned then that version is not supported

### Get uri's for apt-get packages

apt-get --print-uris --yes install mongodb-server | grep ^\' | cut -d\' -f2

apt-rdepends mongodb | grep "[^e]Depends: " | awk '{print $2}' | sort | uniq > ok.tx


### extracting deb or rpms
http://www.g-loaded.eu/2008/01/28/how-to-extract-rpm-or-deb-packages/

### get a list of OS libraries

ldconfig -p

### Filter with grep

grep -v DONT_WANT_TO_SEE

### update clock in ubuntu
sudo ntpdate -s time.nist.gov

### check for open port
telnet <ip> <port>

### time to run operation
time sleep 2

### sort ips address
https://www.madboa.com/geek/sort-addr/
sort -n -t . -k 1,1 -k 2,2 -k 3,3 -k 4,4

### test ha
ab -n 3000 -c 1 https://<host>

### Stress Test rabbitmq
./runjava.sh com.rabbitmq.examples.PerfTest -h amqps://<user>:<password>@<host>:<port>/<vhost> -x 1 -y 1 -s 1000 -C 10 -u <queue-name>`

### exclude from git diff
http://stackoverflow.com/questions/4380945/exclude-a-directory-from-git-diff
git diff previous_release current_release --name-only | grep -v '^spec/' | xargs git diff previous_release current_release --

### set command
var="one two three"
set -- $var
echo "\$1=" $1
echo "\$2=" $2
echo "\$3=" $3
echo "\$0=" $0
echo "\$@=" $@

$1= one
$2= two
$3= three
$0= /path/to/file.sh
$@= one two three

bosh -d <mainfest-file.yml> ssh

### Replace space with new line
$ ls | tr ' ' '\n'
file1
file2
file3

### create SSL cert and private key
ssh-keygen -f private.key
openssl req -x509 -nodes -days 3650 -newkey rsa:4096 -keyout private.key -out cert.crt

### Daemonize Program
http://blog.terminal.com/using-daemon-to-daemonize-your-programs/

### Create user on debian
adduser newuser
usermod -aG sudo newuser

### TCPDump Resource
https://danielmiessler.com/study/tcpdump/#gs.vJM77is

tcpdump -i eth0 host 1.2.3.4 and port 1337

### Make Bootable USB from ISO on MacOS
diskutil list #find usb storage device copy its device path IE /dev/disk3
diskutil unmountDisk <device path>
sudo dd if=~/path/to/iso.iso of=<device path> bs=1m
diskutil eject <device path>

### Parameter Expansion
http://wiki.bash-hackers.org/syntax/pe

### sed
http://www.grymoire.com/Unix/Sed.html#uh-0

### ssh locks
~. - terminate session
~B - send a BREAK to the remote system
~R - request rekey (SSH protocol 2 only)
~# - list forwarded connections
~? - this message
~~ - send the escape character
