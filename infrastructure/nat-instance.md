# Self-Managed NAT Instance

A self-managed NAT instance is used to provide outbound internet access for private subnets. For this project, the NAT instance is NOT necessary, and is NOT best practice.
Ideally, a NAT Gateway should be used to allow for private subnets to have outbound access, or VPC endpoints if no outbound access from private subnets is necessary.

## Reasoning Behind Utilizing
I chose to use a NAT Instance due to its low cost relative to NAT Gateway, and to get hands-on experience in configuring `iptables` for NAT.

## Purpose
- Enable ECS hosts and tasks to pull container images
- Support OS and agent communication
- Avoid public IP exposure for application workloads

## Configuration
- Deployed in a public subnet
- Source/Destination check disabled
- IP forwarding enabled
- iptables MASQUERADE rule configured

### Commands Run
```
sudo systemctl -w net.ipv4.ip_forward=1
echo 'net.ipv4.ip_forward =1 | sudo tee /etc/sysctl.d/99-naf  
IFACE=$(ip route | awk '/default/ {print $5; exit}') 
sudo iptables -t nat -A POSTROUTING -o "$IFACE" -j MASQUERADE
sudo yum -y install iptables-services
sudo service iptables save
sudo systemctl enable --now iptables
```

## Tradeoffs
- Lower cost than managed NAT Gateway
- Requires manual configuration and maintenance
- Not highly available by default

This approach was chosen intentionally for learning and visibility into network behavior.
