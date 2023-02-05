## Configuration

=== "All Routers"
    ```java
    router isis IGP
     address-family ipv4 unicast
      mpls ldp auto-config
     !
    !
    mpls oam
    !
    mpls ldp
     log
      neighbor
    ```

## Verify
=== "LDP Forwarding"
```java
RP/0/RP0/CPU0:PE1#show mpls label table
Wed Feb  1 05:45:35.286 UTC
Table Label   Owner                           State  Rewrite
----- ------- ------------------------------- ------ -------
0     0       LSD(A)                          InUse  Yes
0     1       LSD(A)                          InUse  Yes
0     2       LSD(A)                          InUse  Yes
0     13      LSD(A)                          InUse  Yes
0     24000   LDP(A)                          InUse  Yes
0     24001   LDP(A)                          InUse  Yes
0     24002   LDP(A)                          InUse  Yes
0     24003   LDP(A)                          InUse  Yes
0     24004   LDP(A)                          InUse  Yes
0     24005   LDP(A)                          InUse  Yes
0     24006   LDP(A)                          InUse  Yes
0     24007   LDP(A)                          InUse  Yes
0     24008   LDP(A)                          InUse  Yes
0     24009   LDP(A)                          InUse  Yes
0     24010   LDP(A)                          InUse  Yes
0     24011   LDP(A)                          InUse  Yes
0     24012   LDP(A)                          InUse  Yes
0     24013   LDP(A)                          InUse  Yes
0     24014   LDP(A)                          InUse  Yes
0     24015   LDP(A)                          InUse  Yes
0     24016   LDP(A)                          InUse  Yes
RP/0/RP0/CPU0:PE1#

RP/0/RP0/CPU0:PE1# show mpls forwarding
Wed Feb  1 05:45:45.895 UTC
Local  Outgoing    Prefix             Outgoing     Next Hop        Bytes
Label  Label       or ID              Interface                    Switched
------ ----------- ------------------ ------------ --------------- ------------
24000  Pop         2.2.2.2/32         Gi0/0/0/2    12.0.0.2        18522
24001  24000       3.3.3.3/32         Gi0/0/0/2    12.0.0.2        0
24002  24004       6.6.6.6/32         Gi0/0/0/2    12.0.0.2        0
24003  24002       7.7.7.7/32         Gi0/0/0/2    12.0.0.2        0
24004  24001       4.4.4.4/32         Gi0/0/0/2    12.0.0.2        0
24005  24005       8.8.8.8/32         Gi0/0/0/2    12.0.0.2        0
24006  24003       5.5.5.5/32         Gi0/0/0/2    12.0.0.2        0
24007  Pop         23.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24008  Pop         26.0.0.0/24        Gi0/0/0/2    12.0.0.2        793
24009  24010       67.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24010  24008       37.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24011  Pop         27.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24012  24007       47.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24013  24006       34.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24014  24011       78.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24015  24012       48.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
24016  24009       45.0.0.0/24        Gi0/0/0/2    12.0.0.2        0
RP/0/RP0/CPU0:PE1#
```


=== "CEF"
```java
RP/0/RP0/CPU0:PE1#show cef 5.5.5.5/32
Wed Feb  1 05:46:41.858 UTC
5.5.5.5/32, version 29, internal 0x1000001 0x30 (ptr 0xe7af578) [1], 0x600 (0xdacf608), 0xa28 (0xeae6968)
 Updated Feb  1 02:58:34.731
 remote adjacency to GigabitEthernet0/0/0/2
 Prefix Len 32, traffic index 0, precedence n/a, priority 3
  gateway array (0xd937060) reference count 39, flags 0x68, source lsd (5), 1 backups
                [14 type 5 flags 0x8401 (0xeb294c8) ext 0x0 (0x0)]
  LW-LDI[type=5, refc=3, ptr=0xdacf608, sh-ldi=0xeb294c8]
  gateway array update type-time 1 Feb  1 02:58:34.731
 LDI Update time Feb  1 02:58:34.731
 LW-LDI-TS Feb  1 02:58:34.731
   via 12.0.0.2/32, GigabitEthernet0/0/0/2, 4 dependencies, weight 0, class 0 [flags 0x0]
    path-idx 0 NHID 0x0 [0xf399790 0x0]
    next hop 12.0.0.2/32
    remote adjacency
     local label 24006      labels imposed {24003}

    Load distribution: 0 (refcount 14)

    Hash  OK  Interface                 Address
    0     Y   GigabitEthernet0/0/0/2    remote
RP/0/RP0/CPU0:PE1#
```

=== "Traceroute MPLS"
```java
RP/0/RP0/CPU0:PE1#traceroute mpls ipv4 5.5.5.5/32
Wed Feb  1 05:47:07.839 UTC

Tracing MPLS Label Switched Path to 5.5.5.5/32, timeout is 2 seconds

Codes: '!' - success, 'Q' - request not sent, '.' - timeout,
  'L' - labeled output interface, 'B' - unlabeled output interface,
  'D' - DS Map mismatch, 'F' - no FEC mapping, 'f' - FEC mismatch,
  'M' - malformed request, 'm' - unsupported tlvs, 'N' - no rx label,
  'P' - no rx intf label prot, 'p' - premature termination of LSP,
  'R' - transit router, 'I' - unknown upstream index,
  'X' - unknown return code, 'x' - return code 0

Type escape sequence to abort.

  0 12.0.0.1 MRU 1500 [Labels: 24003 Exp: 0]
L 1 12.0.0.2 MRU 1500 [Labels: 24005 Exp: 0] 23 ms
L 2 27.0.0.7 MRU 1500 [Labels: 24000 Exp: 0] 11 ms
L 3 47.0.0.4 MRU 1500 [Labels: implicit-null Exp: 0] 12 ms
! 4 45.0.0.5 13 ms
RP/0/RP0/CPU0:PE1#

RP/0/RP0/CPU0:PE1#show mpls forwarding prefix 5.5.5.5/32
Wed Feb  1 05:47:16.264 UTC
Local  Outgoing    Prefix             Outgoing     Next Hop        Bytes
Label  Label       or ID              Interface                    Switched
------ ----------- ------------------ ------------ --------------- ------------
24006  24003       5.5.5.5/32         Gi0/0/0/2    12.0.0.2        0
RP/0/RP0/CPU0:PE1#

RP/0/RP0/CPU0:P2#show mpls forwarding prefix 5.5.5.5/32
Wed Feb  1 05:47:29.351 UTC
Local  Outgoing    Prefix             Outgoing     Next Hop        Bytes
Label  Label       or ID              Interface                    Switched
------ ----------- ------------------ ------------ --------------- ------------
24003  24002       5.5.5.5/32         Gi0/0/0/0    23.0.0.3        768
       24005       5.5.5.5/32         Gi0/0/0/3    27.0.0.7        1488
RP/0/RP0/CPU0:P2#

RP/0/RP0/CPU0:P7#show mpls forwarding prefix 5.5.5.5/32
Wed Feb  1 05:47:45.797 UTC
Local  Outgoing    Prefix             Outgoing     Next Hop        Bytes
Label  Label       or ID              Interface                    Switched
------ ----------- ------------------ ------------ --------------- ------------
24005  24000       5.5.5.5/32         Gi0/0/0/4    47.0.0.4        992
RP/0/RP0/CPU0:P7#

RP/0/RP0/CPU0:P4#show mpls forwarding prefix 5.5.5.5/32
Wed Feb  1 05:47:53.011 UTC
Local  Outgoing    Prefix             Outgoing     Next Hop        Bytes
Label  Label       or ID              Interface                    Switched
------ ----------- ------------------ ------------ --------------- ------------
24000  Pop         5.5.5.5/32         Gi0/0/0/0    45.0.0.5        20190
RP/0/RP0/CPU0:P4#
```

!!! info "Traceroute MPLS Multipath"
    Multipath traceroute for reference, since there are equal cost multiple paths available.

=== "Traceroute MPLS Multipath"
```java
RP/0/RP0/CPU0:PE1#traceroute mpls multipath ipv4 5.5.5.5/32 verbose
Wed Feb  1 05:52:20.770 UTC

Starting LSP Path Discovery for 5.5.5.5/32

Codes: '!' - success, 'Q' - request not sent, '.' - timeout,
  'L' - labeled output interface, 'B' - unlabeled output interface,
  'D' - DS Map mismatch, 'F' - no FEC mapping, 'f' - FEC mismatch,
  'M' - malformed request, 'm' - unsupported tlvs, 'N' - no rx label,
  'P' - no rx intf label prot, 'p' - premature termination of LSP,
  'R' - transit router, 'I' - unknown upstream index,
  'X' - unknown return code, 'x' - return code 0

Type escape sequence to abort.

LLL!
Path 0 found,
 output interface GigabitEthernet0/0/0/2 nexthop 12.0.0.2
 source 12.0.0.1 destination 127.0.0.3
  0 12.0.0.1 12.0.0.2 MRU 1500 [Labels: 24003 Exp: 0] multipaths 0
L 1 12.0.0.2 23.0.0.3 MRU 1500 [Labels: 24002 Exp: 0] ret code 8 multipaths 2
L 2 23.0.0.3 34.0.0.4 MRU 1500 [Labels: 24000 Exp: 0] ret code 8 multipaths 1
L 3 34.0.0.4 45.0.0.5 MRU 1500 [Labels: implicit-null Exp: 0] ret code 8 multipaths 1
! 4 45.0.0.5, ret code 3 multipaths 0
LL!
Path 1 found,
 output interface GigabitEthernet0/0/0/2 nexthop 12.0.0.2
 source 12.0.0.1 destination 127.0.0.0
  0 12.0.0.1 12.0.0.2 MRU 1500 [Labels: 24003 Exp: 0] multipaths 0
L 1 12.0.0.2 27.0.0.7 MRU 1500 [Labels: 24005 Exp: 0] ret code 8 multipaths 2
L 2 27.0.0.7 47.0.0.4 MRU 1500 [Labels: 24000 Exp: 0] ret code 8 multipaths 1
L 3 47.0.0.4 45.0.0.5 MRU 1500 [Labels: implicit-null Exp: 0] ret code 8 multipaths 1
! 4 45.0.0.5, ret code 3 multipaths 0

Paths (found/broken/unexplored) (2/0/0)
 Echo Request (sent/fail) (7/0)
 Echo Reply (received/timeout) (7/0)
 Total Time Elapsed 96 ms
RP/0/RP0/CPU0:PE1#
```

