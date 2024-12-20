# FP_5027231001_5027231005_5027231013_5027231072

FINAL PROJECT Komunikasi Data dan Jaringan Komputer 

**KELOMPOK 1**
| Nama | NRP |
|---------------------------|------------|
|Revalina Fairuzy | 5027231001 |
|Salsabila Rahmah | 5027231005 |
|Riskiyatul Nur Oktarani | 5027231013 |
|Aisyah Rahmasari | 5027231072 |

<hr>

### TOPOLOGI

![image](https://github.com/user-attachments/assets/827f2b50-c509-47ee-a41f-7ea352b79c2d)

### Pembagian IP - VLSM

![image](https://github.com/user-attachments/assets/2f6e380b-8a39-4545-a7ee-3c18adcb0772)

### Konfigurasi Routing


KONFIGURASI ROUTER

ROUTER 0
```
! ========================
! Konfigurasi Router 0
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0 (IP Nat Inside)
interface FastEthernet0/0
 ip address 192.168.2.14 255.255.255.252
 ip nat inside
 duplex auto
 speed auto

! Interface FastEthernet0/1 (IP Nat Inside)
interface FastEthernet0/1
 ip address 192.168.2.10 255.255.255.252
 ip nat inside
 duplex auto
 speed auto

! Interface FastEthernet1/0 (IP Nat Outside)
interface FastEthernet1/0
 ip address dhcp
 ip nat outside
 duplex auto
 speed auto

! Interface FastEthernet1/1 (Shutdown)
interface FastEthernet1/1
 no ip address
 duplex auto
 speed auto
 shutdown

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! NAT Configuration
! ========================
ip nat inside source list 1 interface FastEthernet1/0 overload

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.2.0 255.255.255.248 192.168.2.13
ip route 192.168.0.0 255.255.255.128 192.168.2.13
ip route 192.168.0.128 255.255.255.128 192.168.2.13
ip route 192.168.1.0 255.255.255.192 192.168.2.13
ip route 192.168.1.64 255.255.255.192 192.168.2.13
ip route 192.168.1.128 255.255.255.192 192.168.2.13
ip route 192.168.1.192 255.255.255.192 192.168.2.9

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Access List Configuration
! ========================
access-list 1 permit any

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
End
```

### ROUTER CABANG
```
! ========================
! Konfigurasi Router Kantor Cabang
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.9 255.255.255.252
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.1.193 255.255.255.192
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.10
ip route 192.168.2.0 255.255.255.248 192.168.2.10
ip route 192.168.0.128 255.255.255.128 192.168.2.10
ip route 192.168.1.0 255.255.255.192 192.168.2.10
ip route 192.168.1.64 255.255.255.192 192.168.2.10
ip route 192.168.1.128 255.255.255.192 192.168.2.10
ip route 192.168.2.12 255.255.255.252 192.168.2.10
ip route 8.8.0.0 255.255.0.0 192.168.2.10

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ARA TECH
```
! ========================
! Konfigurasi Router ARA Tech
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.13 255.255.255.252
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.2.6 255.255.255.248
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.1
ip route 192.168.0.128 255.255.255.128 192.168.2.2
ip route 192.168.1.0 255.255.255.192 192.168.2.3
ip route 192.168.1.64 255.255.255.192 192.168.2.4
ip route 192.168.1.128 255.255.255.192 192.168.2.5
ip route 192.168.2.8 255.255.255.252 192.168.2.14
ip route 8.8.0.0 255.255.0.0 192.168.2.14

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ROUTER 1
```
! ========================
! Konfigurasi Router 1
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.1 255.255.255.248
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.0.1 255.255.255.128
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.128 255.255.255.128 192.168.2.9
ip route 192.168.1.0 255.255.255.192 192.168.2.3
ip route 192.168.1.64 255.255.255.192 192.168.2.4
ip route 192.168.1.128 255.255.255.192 192.168.2.5
ip route 192.168.1.192 255.255.255.192 192.168.2.6
ip route 8.8.0.0 255.255.0.0 192.168.2.6

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ROUTER 2
```
! ========================
! Konfigurasi Router 2
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Konfigurasi DHCP
! ========================
ip dhcp excluded-address 192.168.0.129 192.168.0.145
ip dhcp pool lantai2
 network 192.168.0.128 255.255.255.128
 default-router 192.168.0.129
 dns-server 8.8.8.8

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.2 255.255.255.248
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.0.129 255.255.255.128
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.1
ip route 192.168.1.0 255.255.255.192 192.168.2.3
ip route 192.168.1.64 255.255.255.192 192.168.2.4
ip route 192.168.1.128 255.255.255.192 192.168.2.5
ip route 192.168.1.192 255.255.255.192 192.168.2.6
ip route 192.168.2.12 255.255.255.252 192.168.2.6
ip route 8.8.0.0 255.255.0.0 192.168.2.6

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ROUTER 3
```
! ========================
! Konfigurasi Router 3
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.3 255.255.255.248
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.1.1 255.255.255.192
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.1
ip route 192.168.0.128 255.255.255.128 192.168.2.2
ip route 192.168.1.64 255.255.255.192 192.168.2.4
ip route 192.168.1.128 255.255.255.192 192.168.2.5
ip route 192.168.1.192 255.255.255.192 192.168.2.6
ip route 192.168.2.12 255.255.255.252 192.168.2.6
ip route 8.8.0.0 255.255.0.0 192.168.2.6

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ROUTER 4
```
! ========================
! Konfigurasi Router 4
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.4 255.255.255.248
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.1.65 255.255.255.192
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.1
ip route 192.168.0.128 255.255.255.128 192.168.2.2
ip route 192.168.1.0 255.255.255.192 192.168.2.3
ip route 192.168.1.128 255.255.255.192 192.168.2.5
ip route 192.168.1.192 255.255.255.192 192.168.2.6
ip route 192.168.2.12 255.255.255.252 192.168.2.6
ip route 8.8.0.0 255.255.0.0 192.168.2.6

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

ROUTER 5
```
! ========================
! Konfigurasi Router 5
! ========================

version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption

! Hostname perangkat
hostname Router

! ========================
! Spanning-Tree Protocol
! ========================
spanning-tree mode pvst

! ========================
! Konfigurasi Interface
! ========================

! Interface FastEthernet0/0
interface FastEthernet0/0
 ip address 192.168.2.5 255.255.255.248
 duplex auto
 speed auto

! Interface FastEthernet0/1
interface FastEthernet0/1
 ip address 192.168.1.129 255.255.255.192
 duplex auto
 speed auto

! Interface Vlan1 (Shutdown)
interface Vlan1
 no ip address
 shutdown

! ========================
! Routing Configuration
! ========================
ip classless
ip route 192.168.0.0 255.255.255.128 192.168.2.1
ip route 192.168.0.128 255.255.255.128 192.168.2.2
ip route 192.168.1.0 255.255.255.192 192.168.2.3
ip route 192.168.1.64 255.255.255.192 192.168.2.4
ip route 192.168.1.192 255.255.255.192 192.168.2.6
ip route 192.168.2.12 255.255.255.252 192.168.2.6
ip route 8.8.0.0 255.255.0.0 192.168.2.6

! ========================
! Flow Export (Optional)
! ========================
ip flow-export version 9

! ========================
! Line Console and VTY
! ========================
line con 0
line aux 0
line vty 0 4
 login

! ========================
! End of Configuration
! ========================
end
```

#A10
Server-PT
```
# Nama Interface
Interface: FastEthernet0 (default port)

# Konfigurasi IPv4
IPv4 Address: 8.8.8.8
Subnet Mask: 255.255.0.0
Default Gateway: 0.0.0.0

# Konfigurasi IPv6
Link-local IPv6 Address: FE80::201:63FF:FE1D:A831
IPv6 Address: ::
Default Gateway IPv6: ::

# DNS
DNS Suffix: (Tidak Dikonfigurasi)
```



#A7
Perangkat Kantor Cabang
```
# ================================
# Konfigurasi Perangkat Kantor Cabang (40 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.194
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.193
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::206:2AFF:FE89:AC64
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```




#A2
Ruang Server & Data Center (10 host)
```
# ================================
# Konfigurasi Ruang Server & Data Center (10 host)
# ================================

# IP Configuration (IPv4)
IP Mode: Static
IPv4 Address: 192.168.0.4
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.1
DNS Server: 8.8.8.8

# IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::2D0:58FF:FE6B:B12E
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```



DEPARTEMEN IT
# ================================
# Konfigurasi Departemen IT (50 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.0.2
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.1
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::230:F2FF:FE5A:2C92
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled



DEPARTEMEN HR
```
# ================================
# Konfigurasi Departemen HR (20 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.0.3
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.1
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::240:BFF:FE98:D913
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


A3
Departemen R&D
```
# ================================
# Konfigurasi Departemen R&D (40 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: DHCP
IPv4 Address: 192.168.0.146 (Diberikan oleh DHCP)
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::201:42FF:FE1A:6C26
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


Departemen Pemasaran
```
# ================================
# Konfigurasi Departemen Pemasaran (30 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: DHCP
IPv4 Address: 192.168.0.147 (Diberikan oleh DHCP)
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::260:3EFF:FE03:6BB
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


Departemen Penjualan
```
# ================================
# Konfigurasi Departemen Penjualan (20 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: DHCP
IPv4 Address: 192.168.0.148 (Diberikan oleh DHCP)
Subnet Mask: 255.255.255.128
Default Gateway: 192.168.0.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::260:5CFF:FEA7:21B1
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```

A4
Departemen Keuangan
```
# ================================
# Konfigurasi Departemen Keuangan (25 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.2
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.1
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::250:FFF:FEC5:13EE
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


Departemen Legal
```
# ================================
# Konfigurasi Departemen Legal (15 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.3
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.1
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::200:CFF:FE82:574C
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


A5
Departemen Customer Support
```
# ================================
# Konfigurasi Departemen Customer Support (30 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.67
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.65
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::203:E4FF:FE70:C6D3
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```

Departemen Manajemen
```
# ================================
# Konfigurasi Departemen Manajemen (10 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.66
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.65
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::20C:85FF:FE77:38C4
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```

A6
Ruang Meeting
```
# ================================
# Konfigurasi Ruang Meeting (10 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.130
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::204:9AFF:FEA9:7ACC
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```

### Dept HR
```
# ================================
# Konfigurasi Dept HR (20 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.131
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::230:F2FF:FE61:C219
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```

### Departemen Cybersecurity
```
# ================================
# Konfigurasi Departemen Cybersecurity (20 host)
# ================================

# Interface: FastEthernet0

## IPv4 Configuration
IP Mode: Static
IPv4 Address: 192.168.1.132
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.1.129
DNS Server: 8.8.8.8

## IPv6 Configuration
IP Mode: Static
IPv6 Address: (Tidak Dikonfigurasi)
Link Local Address: FE80::20C:CFFF:FE92:1689
Default Gateway: (Tidak Dikonfigurasi)
DNS Server: (Tidak Dikonfigurasi)

# 802.1X Security
802.1X Security: Disabled
```


Demo
1- Susunan topologi
2- ⁠Subnetting (IP yg digunakan, prefix terbesar, jmlh total host)
3- Cara konfigurasi static IP (1 cth)
- ⁠sh ip interface brief
5- ⁠Cara konfigurasi static route (1 cth)
- ⁠sh ip route
4- ⁠Cara konfigurasi DHCP server
- ⁠Cek client apakah mendapat IP DHCP
6- ⁠Cara konfigurasi NAT
- ⁠Ping 8.8.8.8 / keluar NAT, sh ip nat translations
7- ⁠Cara konfigurasi GRE tunnel, IP  tunnel yg digunakan

3. Cara Konfigurasi Static IP
Misal, Router 1 konfigurasi pada interface FastEthernet0/1:
Masuk ke mode konfigurasi interface:
Router> enable
Router# configure terminal
Router(config)# interface FastEthernet0/1
Berikan alamat IP statis:
Router(config-if)# ip address 192.168.0.1 255.255.255.128
Router(config-if)# no shutdown
Verifikasi dengan sh ip interface brief:
Router# show ip interface brief


PENGUJIAN

1. Simulasi Ping Antar Perangkat
Uji konektivitas dengan ping antar perangkat yang berbeda subnet.
 Contoh:
Dari PC di Departemen IT (192.168.0.2) ping ke PC di Departemen Keuangan (192.168.1.2).
PC> ping 192.168.1.2
Hasilnya Request Timed Out kalau ada salah konfigurasi. Kalau Reply, berarti routing berhasil.

Dokumentasi dari PC di Departemen IT (192.168.0.2) ping ke PC di Departemen Keuangan (192.168.1.2).

5. Cara Konfigurasi Static Route
Misalkan Router 1 perlu menambahkan route ke subnet 192.168.0.128/25 melalui 192.168.2.2:
Masuk ke mode konfigurasi:
Router> enable
Router# configure terminal
Router(config)# ip route 192.168.0.128 255.255.255.128 192.168.2.2
Verifikasi dengan sh ip route:

Output akan menampilkan routing yang ditambahkan:

 S    192.168.0.128/25 [1/0] via 192.168.2.2


Hasil

 ⁠
Analisis Output show ip route
S - Static Route
S 8.8.0.0/16 [1/0] via 192.168.2.6
Ini menunjukkan static route yang diarahkan ke jaringan 8.8.0.0/16 melalui next hop 192.168.2.6.
Static route ini biasanya digunakan untuk mengarahkan traffic keluar, misalnya akses ke internet.
S 192.168.1.0/26 [1/0] via 192.168.2.3
Route ini digunakan untuk mengarahkan traffic ke subnet 192.168.1.0/26 melalui 192.168.2.3.
S 192.168.1.64/26 [1/0] via 192.168.2.4
Ini menunjukkan static route ke 192.168.1.64/26 melalui 192.168.2.4.
C - Connected Route
C 192.168.0.0/25 is directly connected, FastEthernet0/1
Ini berarti subnet 192.168.0.0/25 langsung terhubung ke interface FastEthernet0/1.
L - Local Route
L 192.168.0.1/32 is directly connected, FastEthernet0/1
Ini adalah route untuk IP address lokal (interface IP) 192.168.0.1.
Static Route ke Subnet
S 192.168.1.128/26 [1/0] via 192.168.2.5
Mengarahkan ke subnet 192.168.1.128/26 melalui 192.168.2.5.
S 192.168.1.192/26 [1/0] via 192.168.2.9
Route ke 192.168.1.192/26 melalui next hop 192.168.2.9.

3. Tes NAT Overload (PAT) dengan Akses Internet
Ping 8.8.8.8 dari salah satu PC client untuk memastikan NAT berjalan.


Verifikasi NAT di router:

 Router# show ip nat translations
Alternatif Tes:


Uji dengan traceroute ke 8.8.8.8 untuk melihat jalur akses keluar.
 PC> tracert 8.8.8.8
 Jalur seharusnya melewati router NAT.

4. Cara Konfigurasi DHCP Server
Misalkan untuk Departemen R&D (192.168.0.128/25):
Masuk ke mode konfigurasi:
Router> enable
Router# configure terminal
Router(config)# ip dhcp excluded-address 192.168.0.129 192.168.0.145
Router(config)# ip dhcp pool lantai2
Router(dhcp-config)# network 192.168.0.128 255.255.255.128
Router(dhcp-config)# default-router 192.168.0.129
Router(dhcp-config)# dns-server 8.8.8.8
Cek client apakah mendapat IP DHCP:
 Pada perangkat client, gunakan perintah:
 ipconfig /renew
 Lalu verifikasi dengan ipconfig di PC.

PENGUJIAN

2. Uji DHCP Server
Matikan konfigurasi IP statis pada perangkat client di lantai 2 (Departemen R&D, Pemasaran, dan Penjualan), lalu set ke Dynamic IP (DHCP).
Cek IP di PC Client:
Pada command prompt:
 ipconfig /release
ipconfig /renew
Pastikan perangkat mendapatkan IP dari rentang 192.168.0.129 - 192.168.0.254 sesuai konfigurasi DHCP.

4. Simulasi GRE Tunnel
Setelah konfigurasi GRE Tunnel di kedua router, tes konektivitas:
Dari Router ARA Tech ping ke IP Tunnel 10.1.1.2 (Router Kantor Cabang):
 Router# ping 10.1.1.2

Verifikasi Tunnel:
 Router# show interface tunnel 0
 Jika status up/up, maka tunnel sudah aktif.

5. Cara Konfigurasi NAT Overload (PAT)
Misalkan NAT pada Router 0:
Konfigurasi ACL untuk IP lokal:

 Router(config)# access-list 1 permit 192.168.0.0 0.0.255.255
Atur NAT overload di interface:

 Router(config)# interface FastEthernet1/0
Router(config-if)# ip nat outside
Router(config)# interface FastEthernet0/0
Router(config-if)# ip nat inside
Router(config)# ip nat inside source list 1 interface FastEthernet1/0 overload
Ping 8.8.8.8 untuk cek NAT:

 Router# ping 8.8.8.8
verifikasi NAT:
 Router# show ip nat translations


PENGUJIAN

5. Alternatif Pengujian dengan Packet Tracer Tools
Simulation Mode:


Gunakan Simulation Mode di Packet Tracer untuk melihat step-by-step proses komunikasi paket data antar perangkat.
Fokus pada ICMP (ping), DHCP, dan paket NAT keluar ke internet.
Port Status:


Cek status setiap interface router/switch dengan sh ip interface brief.
Pastikan semua interface dalam kondisi up dan Protocol up.


6. Cara Konfigurasi GRE Tunnel
1. Konfigurasi GRE Tunnel di Router ARA Tech
# Masuk ke mode konfigurasi
enable
configure terminal

# Konfigurasi interface Tunnel0
interface tunnel 0
 ip address 10.1.1.1 255.255.255.252   # IP GRE Tunnel untuk ARA Tech
 tunnel source FastEthernet0/1        # Sumber Tunnel (IP 192.168.2.6)
 tunnel destination 192.168.2.9       # Tujuan Tunnel (Kantor Cabang)
 no shutdown
exit

# Simpan konfigurasi
write memory

# Verifikasi Status Tunnel
show interface tunnel 0
show ip route
ping 10.1.1.2                        # Uji koneksi ke IP Tunnel Kantor Cabang


2. Konfigurasi GRE Tunnel di Router Kantor Cabang
cisco
Copy code
# Masuk ke mode konfigurasi
enable
configure terminal

# Aktifkan interface FastEthernet0/1 (Source Tunnel)
interface FastEthernet0/1
 ip address 192.168.2.9 255.255.255.252
 no shutdown
exit

# Konfigurasi interface Tunnel0
interface tunnel 0
 ip address 10.1.1.2 255.255.255.252   # IP GRE Tunnel untuk Kantor Cabang
 tunnel source FastEthernet0/1         # Sumber Tunnel (IP 192.168.2.9)
 tunnel destination 192.168.2.6        # Tujuan Tunnel (ARA Tech)
 no shutdown
exit

# Simpan konfigurasi
write memory

# Verifikasi Status Tunnel
show interface tunnel 0
show ip route
ping 10.1.1.1                        # Uji koneksi ke IP Tunnel ARA Tech


3. Verifikasi Akhir
Di ARA Tech:
Cek status tunnel:
show interface tunnel 0

Cek routing table:
show ip route

Ping tujuan Tunnel (Kantor Cabang):
ping 10.1.1.2

Di Kantor Cabang:
Cek status tunnel:
show interface tunnel 0

Cek routing table:
show ip route

Ping tujuan Tunnel (ARA Tech):
ping 10.1.1.1

Penjelasan Konfigurasi
Tunnel Source: Interface atau IP yang digunakan sebagai sumber Tunnel.
Tunnel Destination: IP tujuan tunnel pada router lawan.
IP Tunnel: Subnet point-to-point yang digunakan untuk GRE Tunnel (misal 10.1.1.0/30).

Hasil Akhir yang Diharapkan
Status Tunnel di kedua router: up/up.
Ping antar IP Tunnel berhasil:
ARA Tech ke Kantor Cabang: 10.1.1.2.
Kantor Cabang ke ARA Tech: 10.1.1.1.


PENGUJIAN












