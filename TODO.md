# Networking Model TODO

Status is based on the current Packet Tracer project files, CSV planning files, and exported switch configs in `ARC FSJ CORE/`, `ARC FSJ/`, `Shell FSJ Core/`, and `Shell FSJ/`.

## Build And Physical Topology

- [x] Add all devices to the Packet Tracer topology.
- [x] Physically connect all devices according to `Conexiones_Fisicas.csv`.
- [x] Connect ARC-FSJ core switches to access/server switches:
  - `ARC-FSJ-CORE01 Fa0/1` to `ARC-FSJ-ACC01 Gi0/1`
  - `ARC-FSJ-CORE02 Fa0/1` to `ARC-FSJ-ACC01 Gi0/2`
  - `ARC-FSJ-CORE01 Fa0/2` to `ARC-FSJ-ACC02 Gi0/1`
  - `ARC-FSJ-CORE02 Fa0/2` to `ARC-FSJ-ACC02 Gi0/2`
  - `ARC-FSJ-CORE01 Fa0/3` to `ARC-FSJ-ACC03 Gi0/1`
  - `ARC-FSJ-CORE02 Fa0/3` to `ARC-FSJ-ACC03 Gi0/2`
  - `ARC-FSJ-CORE01 Fa0/4` to `ARC-FSJ-SRV-SW01 Gi0/1`
  - `ARC-FSJ-CORE02 Fa0/4` to `ARC-FSJ-SRV-SW01 Gi0/2`
- [x] Connect Shell-FSJ core switches to access/server switches:
  - `SHL-FSJ-CORE01 Fa0/1` to `SHL-FSJ-ACC01 Gi0/1`
  - `SHL-FSJ-CORE02 Fa0/1` to `SHL-FSJ-ACC01 Gi0/2`
  - `SHL-FSJ-CORE01 Fa0/2` to `SHL-FSJ-ACC02 Gi0/1`
  - `SHL-FSJ-CORE02 Fa0/2` to `SHL-FSJ-ACC02 Gi0/2`
  - `SHL-FSJ-CORE01 Fa0/3` to `SHL-FSJ-ACC03 Gi0/1`
  - `SHL-FSJ-CORE02 Fa0/3` to `SHL-FSJ-ACC03 Gi0/2`
  - `SHL-FSJ-CORE01 Fa0/4` to `SHL-FSJ-SRV-SW01 Gi0/1`
  - `SHL-FSJ-CORE02 Fa0/4` to `SHL-FSJ-SRV-SW01 Gi0/2`
- [x] Connect end devices, APs, servers, and WLCs to their assigned switch ports.
- [x] Connect WAN, firewall, ISP, and VPN-related devices as documented in the physical connections plan.

## VLANs

- [x] Verify VLANs exist on every ARC-FSJ switch with `show vlan brief`.
- [x] Verify VLANs exist on every Shell-FSJ switch with `show vlan brief`.
- [x] Add missing VLANs where needed:

```cisco
vlan 10
 name IT
vlan 20
 name OT
vlan 30
 name SERVERS
vlan 40
 name WIFI
vlan 99
 name MGMT
```

## ARC-FSJ Switching

- [x] Configure `ARC-FSJ-CORE01` trunk ports `Fa0/1`, `Fa0/2`, `Fa0/23`, and `Fa0/24`.
- [x] Configure or verify `ARC-FSJ-CORE01 Fa0/3` and `Fa0/4` as trunks for `ACC03` and `SRV-SW01`.
- [x] Configure `ARC-FSJ-CORE02` trunk ports `Fa0/1`, `Fa0/2`, `Fa0/23`, and `Fa0/24`.
- [x] Configure or verify `ARC-FSJ-CORE02 Fa0/3` and `Fa0/4` as trunks for `ACC03` and `SRV-SW01`.
- [x] Configure `ARC-FSJ-ACC01 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `ARC-FSJ-ACC02 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `ARC-FSJ-ACC03 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `ARC-FSJ-SRV-SW01 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `ARC-FSJ-ACC01 Fa0/24` as access VLAN 40 for `ARC-FSJ-AP01`.
- [x] Configure `ARC-FSJ-ACC02 Fa0/1` and `Fa0/2` as access VLAN 10 for PCs.
- [x] Configure `ARC-FSJ-ACC03 Fa0/1` as access VLAN 20 for OT/PLC.
- [x] Configure `ARC-FSJ-SRV-SW01 Fa0/1` and `Fa0/2` as access VLAN 30 for servers.
- [x] Configure `ARC-FSJ-SRV-SW01 Fa0/3` as a WLC trunk allowing VLANs `30,40,99`.

## Shell-FSJ Switching

- [x] Configure `SHL-FSJ-CORE01` trunk ports `Fa0/1`, `Fa0/2`, `Fa0/23`, and `Fa0/24`.
- [x] Configure or verify `SHL-FSJ-CORE01 Fa0/3` and `Fa0/4` as trunks for `ACC03` and `SRV-SW01`.
- [x] Configure `SHL-FSJ-CORE02` trunk ports `Fa0/1`, `Fa0/2`, `Fa0/23`, and `Fa0/24`.
- [x] Configure or verify `SHL-FSJ-CORE02 Fa0/3` and `Fa0/4` as trunks for `ACC03` and `SRV-SW01`.
- [x] Configure `SHL-FSJ-ACC01 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `SHL-FSJ-ACC02 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `SHL-FSJ-ACC03 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `SHL-FSJ-SRV-SW01 Gi0/1` and `Gi0/2` as trunks.
- [x] Configure `SHL-FSJ-ACC01 Fa0/24` as access VLAN 40 for `SHL-FSJ-AP01`.
- [x] Configure `SHL-FSJ-ACC02 Fa0/1` as access VLAN 10 for `SHL-FSJ-PC01`.
- [x] Configure `SHL-FSJ-ACC03 Fa0/1` as access VLAN 20 for OT/PLC.
- [x] Configure `SHL-FSJ-SRV-SW01 Fa0/1` and `Fa0/2` as access VLAN 30 for servers.
- [x] Configure `SHL-FSJ-SRV-SW01 Fa0/3` as a WLC trunk allowing VLANs `30,40,99`.

## Core Layer 3 And HSRP

- [x] Enable `ip routing` on `ARC-FSJ-CORE01` and `ARC-FSJ-CORE02`.
- [x] Configure ARC-FSJ SVIs for VLANs `10`, `20`, `30`, `40`, and `99`.
- [x] Configure ARC-FSJ HSRP virtual gateways:
  - VLAN 10: `10.10.10.1`
  - VLAN 20: `10.10.20.1`
  - VLAN 30: `10.10.30.1`
  - VLAN 40: `10.10.40.1`
  - VLAN 99: `10.255.10.254`
- [x] Enable `ip routing` on `SHL-FSJ-CORE01` and `SHL-FSJ-CORE02`.
- [x] Configure Shell-FSJ SVIs for VLANs `10`, `20`, `30`, `40`, and `99`.
- [x] Configure Shell-FSJ HSRP virtual gateways:
  - VLAN 10: `10.20.10.1`
  - VLAN 20: `10.20.20.1`
  - VLAN 30: `10.20.30.1`
  - VLAN 40: `10.20.40.1`
  - VLAN 99: `10.255.20.254`
- [ ] Verify HSRP state on all core switches with `show standby brief`.
- [ ] Add default/static routing from cores toward firewalls or edge devices if not already configured.

## Management

- [x] Configure ARC access/server switch management SVIs in VLAN 99:
  - `ARC-FSJ-ACC01`: `10.255.10.31/24`
  - `ARC-FSJ-ACC02`: `10.255.10.32/24`
  - `ARC-FSJ-ACC03`: `10.255.10.33/24`
  - `ARC-FSJ-SRV-SW01`: `10.255.10.34/24`
- [x] Configure Shell access/server switch management SVIs in VLAN 99:
  - `SHL-FSJ-ACC01`: `10.255.20.31/24`
  - `SHL-FSJ-ACC02`: `10.255.20.32/24`
  - `SHL-FSJ-ACC03`: `10.255.20.33/24`
  - `SHL-FSJ-SRV-SW01`: `10.255.20.34/24`
- [x] Configure ARC access/server switch default gateway as `10.255.10.254`.
- [x] Configure Shell access/server switch default gateway as `10.255.20.254`.
- [ ] Verify management reachability by pinging each switch management IP from the local cores.

## Spanning Tree

- [x] Enable PVST mode on core and access/server switches.
- [ ] Fix or verify spanning-tree root priorities:
  - `CORE01` should be root primary for VLANs `10,20,30,40,99`.
  - `CORE02` should be root secondary for VLANs `10,20,30,40,99`.
- [ ] Verify STP with `show spanning-tree vlan 10`, `show spanning-tree vlan 20`, `show spanning-tree vlan 30`, `show spanning-tree vlan 40`, and `show spanning-tree vlan 99`.
- [x] Configure PortFast on known end-device ports shown in the switch exports.
- [ ] Consider adding BPDU Guard on end-device access ports.

## Servers, DHCP, DNS, Mail, And WLC

- [ ] Configure ARC DNS/DHCP server IP settings on VLAN 30.
- [ ] Configure Shell DNS/DHCP server IP settings on VLAN 30.
- [ ] Configure DHCP pools for user, OT, WiFi, and management/client VLANs as required by the design.
- [ ] Configure default gateways in DHCP scopes to use the HSRP VIPs.
- [ ] Configure DNS records or DNS service entries if required by the project.
- [ ] Configure mail server service if required by the project.
- [ ] Configure ARC WLC management/interface settings.
- [ ] Configure Shell WLC management/interface settings.
- [ ] Map wireless SSIDs to the correct VLANs.
- [ ] Verify AP-to-WLC association if using WLC-managed wireless.

## Firewalls, WAN, VPN, And ISP Edge

- [ ] Configure ARC firewalls `ARC-FSJ-FW01` and `ARC-FSJ-FW02`.
- [ ] Configure Shell firewalls `SHL-FSJ-FW01` and `SHL-FSJ-FW02`.
- [ ] Configure firewall inside/outside IP addresses from `Conexiones_Fisicas.csv`.
- [ ] Configure routing between cores and firewalls.
- [ ] Configure ARC edge routers and ISP-facing links.
- [ ] Configure Shell edge routers and ISP-facing links.
- [ ] Configure ISP simulation routers and backbone serial links.
- [ ] Configure BGP between edge routers and ISP routers if required.
- [ ] Configure IPSec VPN tunnels:
  - `ARC-FSJ-FW01 Tunnel10` to `SHL-FSJ-FW01 Tunnel10`
  - `ARC-FSJ-FW02 Tunnel20` to `SHL-FSJ-FW02 Tunnel20`
- [ ] Configure ACLs/security policies for allowed inter-site traffic.
- [x] Document inter-VLAN ACL policy in `ACLs_Inter_VLAN.csv`:
  - VLAN 10 (IT): blocked from OT and MGMT, permitted to Servers/WiFi/WAN.
  - VLAN 20 (OT): isolated; only DNS/DHCP to Servers allowed; blocked from IT/WiFi/MGMT.
  - VLAN 40 (WiFi): blocked from OT and MGMT, permitted to Servers/IT/WAN.
  - VLAN 99 (MGMT): full access (administration).
  - VLAN 30 (Servers): no ACL (must respond to all permitted clients).
- [ ] Apply `ACL_VLAN10_IN`, `ACL_VLAN20_IN`, `ACL_VLAN40_IN`, and `ACL_VLAN99_IN` on ARC core switches.
- [ ] Apply `ACL_VLAN10_IN`, `ACL_VLAN20_IN`, `ACL_VLAN40_IN`, and `ACL_VLAN99_IN` on Shell core switches.

## Verification

- [ ] On every switch, run `show vlan brief`.
- [ ] On every switch with trunks, run `show interfaces trunk`.
- [ ] On every core switch, run `show ip interface brief`.
- [ ] On every core switch, run `show standby brief`.
- [ ] From ARC PCs, ping:
  - VLAN 10 gateway `10.10.10.1`
  - ARC server VLAN gateway `10.10.30.1`
  - ARC DNS/DHCP server
- [ ] From Shell PCs, ping:
  - VLAN 10 gateway `10.20.10.1`
  - Shell server VLAN gateway `10.20.30.1`
  - Shell DNS/DHCP server
- [ ] From ARC access switches, ping `10.255.10.254`.
- [ ] From Shell access switches, ping `10.255.20.254`.
- [ ] Test ARC-to-Shell reachability after routing/firewall/VPN configuration is complete.
- [ ] Save configs on every configured device with `write memory`.
- [ ] Export final device configs with `terminal length 0` and `show running-config`.
