SSH Port Forwarding: Local, Remote, and Dynamic

Secure Shell (SSH) port forwarding, often called SSH tunneling, is a powerful technique that redirects network traffic through an encrypted SSH connection. This method creates a secure tunnel between two computers, allowing you to safely transmit data even across unsecured networks like public Wi-Fi or the internet.

SSH port forwarding has three primary types, each serving different use cases:

Local Port Forwarding (ssh -L): Forwards traffic from your local machine to a remote server. Useful for accessing remote services as if they were running locally.

Remote Port Forwarding (ssh -R): Forwards traffic from a remote server to your local machine. Ideal for exposing local services to remote networks.

Dynamic Port Forwarding (ssh -D): Creates a SOCKS proxy that can forward various types of traffic through the SSH connection. Perfect for secure web browsing or accessing multiple services.

1.Local Port Forwarding (ssh -L)

your route traffic  going to a local port to a remote host using an ssh encrypted tunnel.

#syntax
ssh -L local_port:destination_host:destination_port username@ssh_server


**IMPORTANT NOTE**:the traffic between the remote host and the ssh server is not encrypted its uses normal tcp, only the traffic from the local machine to the ssh server is encrypted.


2.Remote Port Forwarding (ssh -R)

Remote port forwarding creates a secure tunnel that routes traffic from a remote server back to your local machine. This type of forwarding is particularly useful in scenarios where you need to expose local services to external users or systems.


#syntax

ssh -R remote_port:local_host:local_port username@remote_ssh_server

To enable remote port forwarding you need to enable (GatewayPorts yes) in /etc /ssh/sshd_config and restart ssh.



3.Dynamic Port Forwarding (ssh -D)

Dynamic port forwarding creates a SOCKS proxy that routes network traffic through a secure SSH tunnel, effectively anonymizing your connection. This powerful feature creates a local SOCKS proxy server on your machine that forwards all traffic through the SSH connection to the remote server, which then makes the actual requests to the internet. This method is particularly useful for:

Secure Browsing: Encrypting all your web traffic when using public or untrusted networks
Bypassing Network Restrictions: Accessing resources that might be blocked in your current network
Privacy Protection: Hiding your actual IP address by routing traffic through the remote server
Application-Level Proxying: Allowing individual applications to route their traffic through the secure tunnel
The SOCKS proxy created by dynamic port forwarding is more flexible than local or remote port forwarding because it can handle multiple types of traffic and protocols, not just specific ports. It works at the application layer, making it compatible with most network applications that support SOCKS proxies.

#syntax
ssh -D 8080 user@secure-server.com


but we nee to configure our app or browser use the proxy from its config


