# Single Segment TI-LFA (Topology Independent - LoopFree Alternate)

<figure markdown>
  ![single_segment_tilfa.png](assets/images/single_segment_tilfa.png){ loading=lazy }
  <figcaption>Single Segment TI-LFA</figcaption>
</figure>

Single Segment TI-LFA is a backup route in which the router delivers traffic to the destination after adding one additional segment to the original segment in the event of a local link failure.


## Prepare the topology
Because there were numerous short paths to P4, create a ring topology by closing off three isis adjacencies on P7.

To protect the link between P2 and P3, the P2 router now has a backup route through P8, which is the post-convergence path in the event of the previously described link failure.

=== "P7"
    ```java
    router isis IGP
     interface GigabitEthernet0/0/0/1
      shutdown
     !
     interface GigabitEthernet0/0/0/3
      shutdown
     !
     interface GigabitEthernet0/0/0/4
      shutdown
    ```

## Verify

=== "P2's P-space"
    ```
    Routers P2 can reach without using P2 - P3 link (excluding ECMP)
        1. P6
        2. P7
    ```

=== "P-space of P6 (P2's neighbor)"
    ```
    Routers P6 can reach without using P2 - P3 link
        1. P7
        2. P8
    ```

=== "Extended P-space of P2, with respect to P2 - P3 link"
    ```
    1. P6
    2. P7
    3. P8
    ```

P8 is in Extended-P-space (or P-node) (P2 can send packets to P8 without any risk of packet flowing via P2 – P3).

P8 is also in Q-space (P8 can send packets to destination PE5, without any risk of packet flowing via P2 – P3).

P2 would need to tunnel the original segment to P8 across the intermediate hops, which is why it imposes an extra segment, thus the term single segment ti-lfa.

The backup route on P2 includes the Prefix-SID of P8 as the top label and the Prefix-SID of PE5 as the bottom label, directing traffic first to P8 and then to PE5, with no possibility of it passing via P2 - P3.


=== "Single Segment TI-LFA"
```java
RP/0/RP0/CPU0:P2#show isis fast-reroute 5.5.5.5/32 detail
Wed Feb  1 07:33:32.000 UTC

L2 5.5.5.5/32 [30/115] Label: 16005, medium priority
   Installed Feb 01 07:33:06.856 for 00:00:26
     via 23.0.0.3, GigabitEthernet0/0/0/0, Label: 16005, P3, SRGB Base: 16000, Weight: 0
       Backup path: TI-LFA (link), via 26.0.0.6, GigabitEthernet0/0/0/1 P6, SRGB Base: 16000, Weight: 0, Metric: 50
         P node: P8.00 [8.8.8.8], Label: 16008  // (1)
         Prefix label: 16005
         Backup-src: PE5.00
       P: No, TM: 50, LC: No, NP: No, D: No, SRLG: Yes
     src PE5.00-00, 5.5.5.5, prefix-SID index 5, R:0 N:1 P:0 E:0 V:0 L:0, Alg:0
RP/0/RP0/CPU0:P2#

RP/0/RP0/CPU0:P2#show cef 5.5.5.5/32
Wed Feb  1 07:33:45.503 UTC
5.5.5.5/32, version 444, labeled SR, internal 0x1000001 0x8310 (ptr 0xe727de0) [1], 0x600 (0xe190578), 0xa28 (0xf54a0a8)
 Updated Feb  1 07:33:06.863
 remote adjacency to GigabitEthernet0/0/0/0
 Prefix Len 32, traffic index 0, precedence n/a, priority 1
  gateway array (0xdff97f0) reference count 6, flags 0x500068, source rib (7), 1 backups
                [3 type 5 flags 0x8401 (0xeb73a68) ext 0x0 (0x0)]
  LW-LDI[type=5, refc=3, ptr=0xe190578, sh-ldi=0xeb73a68]
  gateway array update type-time 1 Feb  1 07:33:06.863
 LDI Update time Feb  1 07:33:06.863
 LW-LDI-TS Feb  1 07:33:06.863
   via 23.0.0.3/32, GigabitEthernet0/0/0/0, 14 dependencies, weight 0, class 0, protected [flags 0x400]
    path-idx 0 bkup-idx 1 NHID 0x0 [0xdda5820 0x0]
    next hop 23.0.0.3/32
     local label 16005      labels imposed {16005}       // (2)
   via 26.0.0.6/32, GigabitEthernet0/0/0/1, 11 dependencies, weight 0, class 0, backup (TI-LFA) [flags 0xb00]
    path-idx 1 NHID 0x0 [0xf399970 0x0]
    next hop 26.0.0.6/32, Repair Node(s): 8.8.8.8
    remote adjacency
     local label 16005      labels imposed {16008 16005}  // (3)

    Load distribution: 0 (refcount 3)

    Hash  OK  Interface                 Address
    0     Y   GigabitEthernet0/0/0/0    remote
RP/0/RP0/CPU0:P2#
```

1. 1 additional segment added to the original prefix-sid on the backup path
2. Primary route has destination prefix-sid label
3. Backup route has an additional label in the data-plane
