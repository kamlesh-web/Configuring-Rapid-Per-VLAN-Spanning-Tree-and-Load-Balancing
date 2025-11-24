    
    Switch>
    Switch>
    Switch>enable
    Switch#
    Switch#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    Switch(config)#
    Switch(config)#spanning-tree mode rapid-pvst
    Switch(config)#
    Switch(config)#hostname Switch1
    Switch1(config)#
    Switch1(config)#enable secret CCNA
    Switch1(config)#
    Switch1(config)#interface range f0/1,f0/5-24
    Switch1(config-if-range)#
    Switch1(config-if-range)#description ## Not in use ##
    Switch1(config-if-range)#
    Switch1(config-if-range)#shutdown
    
    %LINK-5-CHANGED: Interface FastEthernet0/1, changed state to administratively down
    
    %LINK-5-CHANGED: Interface FastEthernet0/5, changed state to administratively down
    
    (trancated...)
    
    %LINK-5-CHANGED: Interface FastEthernet0/23, changed state to administratively down
    
    %LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down
    Switch1(config-if-range)#
    Switch1(config-if-range)#
    Switch1(config-if-range)#interface range f0/3-4
    Switch1(config-if-range)#
    Switch1(config-if-range)#switchport mode access
    Switch1(config-if-range)#
    Switch1(config-if-range)#switchport access vlan 20
    % Access VLAN does not exist. Creating vlan 20
    Switch1(config-if-range)#	
    Switch1(config-if-range)#vlan 20
    Switch1(config-vlan)#
    Switch1(config-vlan)#name SALES
    Switch1(config-vlan)#
    Switch1(config-vlan)#exit
    Switch1(config)#
    Switch1(config)#interface range f0/2,g0/1-2
    Switch1(config-if-range)#
    Switch1(config-if-range)#switchport mode trunk
    
    
    Switch1(config-if-range)#
    %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to down
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to down
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to up
    
    Switch1(config-if-range)#exit
    Switch1(config)#
    Switch1(config)#spanning-tree vlan 20 root primary
    Switch1(config)#
    Switch1(config)#spanning-tree vlan 10 root secondary
    Switch1(config)#
    Switch1(config)#end
    Switch1#
    %SYS-5-CONFIG_I: Configured from console by console
    
    Switch1#
    Switch1#write
    Building configuration...
    [OK]
    Switch1#
    Switch1#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    Switch1(config)#
    Switch1(config)#vlan 10
    Switch1(config-vlan)#
    Switch1(config-vlan)#name IT
    Switch1(config-vlan)#
    Switch1(config-vlan)#do write
    Building configuration...
    [OK]
    Switch1(config-vlan)#
    Switch1(config-vlan)#end
    Switch1#
    %SYS-5-CONFIG_I: Configured from console by console
    
    Switch1#
    Switch1#show vlan brief
    
    VLAN Name                             Status    Ports
    ---- -------------------------------- --------- -------------------------------
    1    default                          active    Fa0/1, Fa0/5, Fa0/6, Fa0/7
                                                    Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                    Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                    Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                    Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                    Fa0/24
    10   IT                               active    
    20   SALES                            active    Fa0/3, Fa0/4
    1002 fddi-default                     active    
    1003 token-ring-default               active    
    1004 fddinet-default                  active    
    1005 trnet-default                    active    
    Switch1#
    Switch1#show spanning-tree
    VLAN0001
      Spanning tree enabled protocol rstp
      Root ID    Priority    32769
                 Address     0001.4204.7895
                 Cost        4
                 Port        26(GigabitEthernet0/2)
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
    
      Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
                 Address     0030.A364.51C4
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
                 Aging Time  20
    
    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/2            Desg FWD 19        128.2    P2p
    Gi0/1            Desg FWD 4         128.25   P2p
    Gi0/2            Root FWD 4         128.26   P2p
    
    VLAN0010
      Spanning tree enabled protocol rstp
      Root ID    Priority    24586
                 Address     0001.4204.7895
                 Cost        4
                 Port        26(GigabitEthernet0/2)
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
    
      Bridge ID  Priority    28682  (priority 28672 sys-id-ext 10)
                 Address     0030.A364.51C4
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
                 Aging Time  20
    
    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/2            Desg FWD 19        128.2    P2p
    Gi0/1            Desg FWD 4         128.25   P2p
    Gi0/2            Root FWD 4         128.26   P2p
    
    VLAN0020
      Spanning tree enabled protocol rstp
      Root ID    Priority    24596
                 Address     0030.A364.51C4
                 This bridge is the root
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
    
      Bridge ID  Priority    24596  (priority 24576 sys-id-ext 20)
                 Address     0030.A364.51C4
                 Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
                 Aging Time  20
    
    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/3            Desg FWD 19        128.3    P2p
    Fa0/4            Desg FWD 19        128.4    P2p
    Fa0/2            Desg FWD 19        128.2    P2p
    Gi0/1            Desg FWD 4         128.25   P2p
    Gi0/2            Desg FWD 4         128.26   P2p
    
    Switch1#
    Switch1#
