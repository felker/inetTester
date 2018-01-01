## InetAddress tester
Small class (and jar) to quickly check the elapsed time spent from the Java layer to access the localhost domain name.

I had few issues after upgrading from MacOS X El Capitan to MacOS Sierra and now the elapsed time passed from ~5ms-30ms to ~5000ms

### Usage:

`java -jar bin/inetTester.jar`

#### Solution to the issue:

If the call is slow on your Mac (or other OS?) it could be solved by adding the hostname that the application will return on your hosts file, pointing to 127.0.0.1 like:

```
127.0.0.1   localhost mbpro.local
::1         localhost mbpro.local
```

#### Results on MacBook Pro 2017
Using this to debug possible issues with JabRef crashing on macOS High Sierra.
```
K-MBP% hostname
K-MBP.local
K-MBP% java -version
java version "1.8.0_144"
Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed mode)
```
Original `/etc/hosts` file (need sudo access to edit):
```
K-MBP% java -jar bin/inetTester.jar
Calling the hostname resolution method...
Method called, hostname K-MBP.local, elapsed time: 12 (ms)
```

New `/etc/hosts` file
```
K-MBP% java -jar bin/inetTester.jar
Calling the hostname resolution method...
Method called, hostname K-MBP.local, elapsed time: 12 (ms)
```