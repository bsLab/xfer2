# xfer2
A simple network file transfer utility

Xfer2 provides peer-to-peer file transfer between two nodes by using the tar program locally creating a data stream that is transferred over a network socket.

The first node acts a server providing the stream serialized by tar, the second node consumes the data stream and deserializes the stream by using tar again. Xfer2 requires nodejs and tar.

## Server (File Provider)

```
xfer2 -ip IP | -s[erver] <dir> <dir> <file> ..
```

The IP address specifies the public IP address. If IP==0, then xfer tries to lookup the IP address. This can succeed or not. Instead of using the `-ip` option with an IP address (null), the `-s` option without an argument can be used.

## Client (File Consumer)

```
xfer2 <IP or hostname>
```

The client have only to specify the remote IP address of the xfer2 server (see above)

## Reverse Connection

If the file provider is behind a NAT or a firewall, and the file consumer is publically visible, the reverse program `xfer2rev` can be used instead.

```
usage client: xfer2rev -ip IP [-N file] <dir> <dir> <file> .. 
usage server: xfer2rev -ip IP
IP=0: autodetect (server)
```


