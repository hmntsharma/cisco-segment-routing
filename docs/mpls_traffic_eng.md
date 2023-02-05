# MPLS Traffic-Engineering

One of the labs in the following sections requires the routers to be configured for mpls traffic engineering.

The label stack may hold a maximum of three labels, as seen in the double segment ti-lfa lab.

When the number of labels necessary to restore a backup tunnel grows, the Cisco IOS XR platform initiates an auto-tunnel and uses the tunnel interface as the next-hop.

=== "All Routers"
```java
ipv4 unnumbered mpls traffic-eng Loopback0
router isis IGP address-family ipv4 unicast mpls traffic-eng router-id Loopback0
mpls traffic-eng
```
