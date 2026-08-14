# Cybersecurity Lab Setup – Week 1

## Objective

This lab demonstrates the setup and verification of a Kali Linux virtual machine using Oracle VirtualBox and a NAT Network. The network configuration was manually configured and verified using Linux networking commands.

---

# Step 1 – Create CyberLab NAT Network

A NAT Network named **CyberLab-NAT** was created in Oracle VirtualBox.

The network was configured with the IPv4 network:

`10.0.0.0/24`

DHCP was enabled so that the Kali Linux machine could be configured with a static IP address.

![CyberLab NAT Network](01_cyberlab_nat_network.png)

---

# Step 2 – Start Kali Linux Virtual Machine

The Kali Linux virtual machine was started in Oracle VirtualBox.

![Kali Linux VM Running](02_kali_vm_running.png)

---

# Step 3 – Attach Kali Linux to the NAT Network

The Kali Linux virtual machine's network adapter was configured as:

- Attached to: **NAT Network**
- Network Name: **CyberLab-NAT**
- Virtual Cable Connected: Enabled

![Kali Adapter 1 NAT Network](03_kali_adapter1_nat_network.png)

---

# Step 4 – Access the Kali Linux Desktop

After starting the virtual machine, the Kali Linux desktop was successfully accessed.

![Kali Linux Desktop](04_kali_linux_desktop.png)

---

# Step 5 – Configure the Wired IPv4 Connection

The wired network connection was configured manually using the following IPv4 settings:

- IP Address: `10.0.0.2`
- Netmask: `255.255.255.0` (`/24`)
- Gateway: `10.0.0.1`
- DNS Server: `8.8.8.8`

The connection was configured using the **Manual** IPv4 method.

![Wired IPv4 Configuration](05_wired_ipv4_configuration.png)

---

# Step 6 – Configure and Test the Network

The following commands were executed in the Kali Linux terminal to configure and test the network connection:

`ping -c 4 google.com`

`sudo ifconfig eth0 10.0.0.2 netmask 255.255.255.0`

`ifconfig eth0`

`sudo ip route add default via 10.0.0.1`

These commands were used to test network connectivity, configure the IP address, verify the network interface, and configure the default gateway.

![Ping Google and Network Configuration](06_ping_google.png)

---

# Step 7 – Verify the IP Routing Table

The final IP address and routing configuration were verified using the `ip route` command.

The system was found to have the IP address:

`10.0.0.2`

The default gateway was:

`10.0.0.1`

The following command was used to verify the final routing table:

`ip route`

The final routing table showed:

`default via 10.0.0.1 dev eth0`

`10.0.0.0/24 dev eth0 proto kernel scope link src 10.0.0.2`

![Final IP Route](07_final_ip_route.png)

---

# Final Result

The Kali Linux virtual machine was successfully configured with the required network settings.

- **IP Address:** `10.0.0.2`
- **Netmask:** `255.255.255.0`
- **Gateway:** `10.0.0.1`
- **Network:** `10.0.0.0/24`
- **Interface:** `eth0`

The successful connectivity test and final routing table verified the network configuration.
