## Network Configuration: Single Area OSPF

### Overview

This document provides a step-by-step guide for configuring Single Area OSPF on a Cisco router. In this example, all routers are configured within a single OSPF area (area 0).

### Configuration Steps

1. **Enter Global Configuration Mode:**
    ```plaintext
    Router0# en
    Router0# conf t
    ```
2. **Enable OSPF and Specify Router ID:**
    ```plaintext
    Router(config)# router ospf 1
    Router(config-router)# router-id 1.1.1.1
    ```
3. **Specify Network Addresses and Area:**
    - **Network 192.168.1.0/24**: Assigned to area 0
    - **Network 20.0.0.0/24**: Assigned to area 0

    ```plaintext
    Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
    Router(config-router)# network 20.0.0.0 0.0.0.255 area 0
    ```
4. **Remove Incorrect Network Statement:**
    - **Network 10.0.0.0/24**: Assigned to area 0 (to be removed)

    ```plaintext
    Router(config-router)# no network 10.0.0.0 0.0.0.255 area 0
    ```

5. **Exit Configuration Mode:**
    ```plaintext
    Router(config-router)# exit
    Router(config)# exit
    ```
6. **Save Configuration to Memory:**
    ```plaintext
    Router# write memory
    ```

    ![Single Area OSPF Network Diagram](/SingleAreaOSPF-Network/images/SingleAreaOSPF.png)

### Explanation
- **Router ID**: A unique identifier for the OSPF router, often set to an IP address for simplicity.
- **Network Statements**: The `network` commands specify which interfaces participate in OSPF and the area they belong to. Here, all networks are part of area 0.
- **Removing Incorrect Network Statement**: The `no network 10.0.0.0 0.0.0.255 area 0` command removes the incorrect network statement from the OSPF configuration.
- **Saving Configuration**: The `write memory` command ensures the configuration is saved and persists after a reboot.
