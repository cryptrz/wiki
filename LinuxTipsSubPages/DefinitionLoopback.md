# Definition

The [loopback device](http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface) is a special, [virtual](https://en.wikipedia.org/wiki/Virtual_Interface) [network interface](http://en.wikipedia.org/wiki/Computer_port_%28hardware%29)
 that your computer uses to communicate with itself. It is used mainly 
for diagnostics and troubleshooting, and to connect to servers running 
on the local machine.

## The Purpose of Loopback

When a network interface is disconnected--for example, when an [Ethernet](http://en.wikipedia.org/wiki/Ethernet) port is unplugged or [Wi-Fi](http://en.wikipedia.org/wiki/Wifi) is turned off or not associated with an [access point](http://en.wikipedia.org/wiki/Wireless_access_point)--no
 communication on that interface is possible, not even communication 
between your computer and itself. The loopback interface does not 
represent any actual hardware, but exists so applications running on 
your computer can always connect to servers on the same machine.

This is important for troubleshooting (it can be compared to looking 
in a mirror). The loopback device is sometimes explained as purely a 
diagnostic tool. But it is also helpful when a server offering a 
resource you need *is running on your own machine*.

For example, if you run a web server, you have all your web documents
 and could examine them file by file. You may be able to load the files 
in your browser too, though with server-side active content, it won't 
work the way it does when someone accesses it normally.

So if you want to experience the same site others do, the best course
 is usually to connect to your own server. The loopback interface 
facilitates that.

## Addresses on Loopback

For [IPv4](http://en.wikipedia.org/wiki/IPv4), the loopback interface is assigned all the [IPs](http://en.wikipedia.org/wiki/IP_address) in the `127.0.0.0/8` [address block](http://en.wikipedia.org/wiki/Subnetwork). That is, `127.0.0.1` through `127.255.255.254` *all* represent your computer. For most purposes, though, it is only necessary to use one IP address, and that is `127.0.0.1`. This IP has the [hostname](http://en.wikipedia.org/wiki/Hostname) of [`localhost`](http://en.wikipedia.org/wiki/Localhost) mapped to it.

Thus, to log in as `bob` via [SSH](https://help.ubuntu.com/community/SSH) to the SSH server running on your own machine, you would use:

```
ssh bob@localhost

```

Like other network adapters, the loopback device shows up in the output of [`ifconfig`](http://manpages.ubuntu.com/manpages/precise/en/man8/ifconfig.8.html). Its name is [`lo`](http://manpages.ubuntu.com/manpages/precise/en/man4/lo.4freebsd.html).

```
ek@Del:~$ ifconfig lo
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4381349 (4.3 MB)  TX bytes:4381349 (4.3 MB)

```

## An Example: CUPS

One common, production (i.e., not just diagnostic) use of `localhost` on Ubuntu is to perform advanced printer configuration. In a web browser, go to:

```
http://localhost:631

```

[CUPS](http://en.wikipedia.org/wiki/CUPS)
 runs a web server on port 631, and this can be used to configure 
printing, regardless of what GUI you are running (or even if you are not
 running a GUI at all).

![](https://i.sstatic.net/3BDda.png)

If you try connecting to `http://127.0.0.1:631`, this will work too. However, if you try to connect to `http://127.0.0.2`, it will not. All the `127.*.*.*`
 addresses identify your computer on the loopback interface, but a 
server program can decide to bind just to a specific IP address.

## A Notable Difference from Windows

If you come from a Windows background, you might expect `loopback` to itself be a synonym of `localhost` (and thus to be able to ping `loopback`, connect to servers on `loopback`, and so forth). That behavior is peculiar to Windows.

- But you *can* [add any name](http://en.wikipedia.org/wiki/Hosts_file) including `loopback` to your [`/etc/hosts` file](http://manpages.ubuntu.com/manpages/precise/en/man5/hosts.5.html), with `127.0.0.1` as its address, and it will act like `localhost`.

## Other Meanings of "Loopback"

The general concept of [*loopback*](http://en.wikipedia.org/wiki/Loopback) is a mechanism through which a message or signal ends up (or loops) back to where it started.

So there are a few other ways *loopback* is use in Ubuntu that should not be confused with the loopback device in networking.

### Loop Mounts

To mount a disk image in Ubuntu, you could run:

```
sudo mount -o loopimage.iso /media/label
```

This is usually called a [*loop device*](http://en.wikipedia.org/wiki/Loop_device) (and not a *loopback device*), but the term *loopback file interface* is occasionally used.

This has nothing to do with the loopback device in networking.

### Sound

Pulseaudio and other sound systems provide a mechanism to "connect" 
line-in to line-out, so that audio input is echoed back to your 
speakers/headphones. Pulseaudio's [loopback module](http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ#How_do_I_connect_an_input_source_to_an_output_sink.3F) facilitates this.

Here, it *is* correct to use the term *loopback*, but 
like loop mounts, this also has nothing to do with the loopback device 
in networking. (And nothing to do with loop mounts, either.)

## Further Reading

- [TLDP](http://www.tldp.org/guides.html), "[The Loopback Interface](http://www.tldp.org/LDP/nag/node66.html)"
- [How is the loopback device implemented?](https://askubuntu.com/questions/181041/how-is-the-loopback-device-implemented)