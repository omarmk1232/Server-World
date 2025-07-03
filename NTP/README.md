so linux has two types of clocks

1.Hardware Clock(RTC): a small battery-backed clock on your motherboard that keeps track of time even when the system is powered off

2.System Clock:(software clock): this clock is maintained by the linux kernal ,It starts up from the hardware clock at boot and then runs independently and all your system applications relay on it.


Ntp:(Netwrok Time Protocol): is an application layer protocol in the TCP/IP protocol suite ,it  keeps your server’s system clock accurate by regularly synchronizing it with remote time servers over the internet or LAN which can be used to unify the systime on all your hosts accross the network.


why do we use an NTP Server:
Without NTP, each server relies on its local hardware clock, which drifts over time leading to systems having different times. This causes problems for logs, security , and distributed applications that depend on synchronized time. An NTP server (or a pool of them) acts as a trusted, precise source of time, and all servers synchronize with it, ensuring they all stay within milliseconds of the correct time and of each other. In short: we use NTP servers to avoid time drift and keep all systems on the same clock.


















