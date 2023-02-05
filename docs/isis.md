## Configuration

!!! info "NET Schema"
    The ISIS NET schema for each node is : 49.0000.0000.000x.00, where x is the number associated with the router in the base topology image.



=== "PE1"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0001.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P2"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0002.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/3
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P3"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0003.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P4"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0004.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/4
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "PE5"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0005.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P6"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0006.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P7"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0007.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/0
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/3
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/4
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```

=== "P8"
    ```java
    router isis IGP
     is-type level-2-only
     net 49.0000.0000.0008.00
     log adjacency changes
     address-family ipv4 unicast
      metric-style wide level 2
     !
     interface Loopback0
      passive
      address-family ipv4 unicast
      !
     !
     interface GigabitEthernet0/0/0/1
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
      !
     !
     interface GigabitEthernet0/0/0/2
      circuit-type level-2-only
      point-to-point
      hello-padding disable
      address-family ipv4 unicast
       metric 10
    ```


## Verify

=== "Routing Table"
    ```java
    RP/0/RP0/CPU0:PE1#show route
    Wed Feb  1 05:43:59.895 UTC
    
    Codes: C - connected, S - static, R - RIP, B - BGP, (>) - Diversion path
           D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
           N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
           E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
           i - ISIS, L1 - IS-IS level-1, L2 - IS-IS level-2
           ia - IS-IS inter area, su - IS-IS summary null, * - candidate default
           U - per-user static route, o - ODR, L - local, G  - DAGR, l - LISP
           A - access/subscriber, a - Application route
           M - mobile route, r - RPL, t - Traffic Engineering, (!) - FRR Backup path
    
    Gateway of last resort is not set
    
    L    1.1.1.1/32 is directly connected, 02:46:30, Loopback0
    i L2 2.2.2.2/32 [115/10] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 3.3.3.3/32 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 4.4.4.4/32 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 5.5.5.5/32 [115/40] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 6.6.6.6/32 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 7.7.7.7/32 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 8.8.8.8/32 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    C    12.0.0.0/24 is directly connected, 02:45:39, GigabitEthernet0/0/0/2
    L    12.0.0.1/32 is directly connected, 02:45:39, GigabitEthernet0/0/0/2
    i L2 23.0.0.0/24 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 26.0.0.0/24 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 27.0.0.0/24 [115/20] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 34.0.0.0/24 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 37.0.0.0/24 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 45.0.0.0/24 [115/40] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 47.0.0.0/24 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 48.0.0.0/24 [115/40] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 67.0.0.0/24 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    i L2 78.0.0.0/24 [115/30] via 12.0.0.2, 02:45:29, GigabitEthernet0/0/0/2
    L    127.0.0.0/8 [0/0] via 0.0.0.0, 02:46:33
    C    192.168.18.0/24 is directly connected, 02:46:27, MgmtEth0/RP0/CPU0/0
    L    192.168.18.1/32 is directly connected, 02:46:27, MgmtEth0/RP0/CPU0/0
    RP/0/RP0/CPU0:PE1#
    
    RP/0/RP0/CPU0:PE1#show isis route 5.5.5.5/32 detail
    Wed Feb  1 05:44:24.867 UTC
    
    L2 5.5.5.5/32 [40/115] Label: None, medium priority
       Installed Feb 01 02:58:30.358 for 02:45:54
         via 12.0.0.2, GigabitEthernet0/0/0/2, P2, Weight: 0
         src PE5.00-00, 5.5.5.5
    RP/0/RP0/CPU0:PE1#
    
    RP/0/RP0/CPU0:PE1#show route 5.5.5.5/32 detail
    Wed Feb  1 05:44:45.325 UTC
    
    Routing entry for 5.5.5.5/32
      Known via "isis IGP", distance 115, metric 40, type level-2
      Installed Feb  1 02:58:30.358 for 02:46:15
      Routing Descriptor Blocks
        12.0.0.2, from 5.5.5.5, via GigabitEthernet0/0/0/2
          Route metric is 40
          Label: None
          Tunnel ID: None
          Binding Label: None
          Extended communities count: 0
          Path id:1       Path ref count:0
          NHID:0x1(Ref:18)
      Route version is 0x1 (1)
      No local label
      IP Precedence: Not Set
      QoS Group ID: Not Set
      Flow-tag: Not Set
      Fwd-class: Not Set
      Route Priority: RIB_PRIORITY_NON_RECURSIVE_MEDIUM (7) SVD Type RIB_SVD_TYPE_LOCAL
      Download Priority 1, Download Version 18
      No advertising protos.
    RP/0/RP0/CPU0:PE1#
    ```
