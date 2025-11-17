# Jarkom-Modul-4-2025-K-01

| Nama                                  | NRP        |
| ------------------------------------- | ---------- | 
| Muhammad Fatihul Qolbi Ash Shiddiqi   | 5027241023 | 
| Hansen Chang                          | 5027241028 | 

## Rute
<img width="798" height="578" alt="image" src="https://github.com/user-attachments/assets/c6daefd3-4750-446b-b69a-72e7c869ba35" />

## GNS ( VLSM )
Untuk metode VLSM, kami menggunakan GNS3 sebagai platformnya

### Topologi
<img width="2301" height="1301" alt="VLSM drawio" src="https://github.com/user-attachments/assets/ad706ebf-77da-486f-9a70-48db8801bf2b" />

### Pembagian IP 
<img width="850" height="625" alt="image" src="https://github.com/user-attachments/assets/8bce2cca-b3cf-4b35-a27a-d62a397826f9" />

Atau Lebih Jelasnya 

| Subnet | Network ID     | Netmask         | Broadcast     | Range IP                     |
|--------|----------------|-----------------|---------------|------------------------------|
| A9     | 10.64.0.0      | 255.255.252.0   | 10.64.3.255   | 10.64.0.1 – 10.64.3.254      |
| A12    | 10.64.4.0      | 255.255.252.0   | 10.64.7.255   | 10.64.4.1 – 10.64.7.254      |
| A10    | 10.64.8.0      | 255.255.254.0   | 10.64.9.255   | 10.64.8.1 – 10.64.9.254      |
| A11    | 10.64.10.0     | 255.255.254.0   | 10.64.11.255  | 10.64.10.1 – 10.64.11.254    |
| A1     | 10.64.12.0     | 255.255.254.0   | 10.64.13.255  | 10.64.12.1 – 10.64.13.254    |
| A6     | 10.64.14.0     | 255.255.255.128 | 10.64.14.127  | 10.64.14.1 – 10.64.14.126    |
| A5     | 10.64.14.128   | 255.255.255.128 | 10.64.14.255  | 10.64.14.129 – 10.64.14.254  |
| A13    | 10.64.15.0     | 255.255.255.192 | 10.64.15.63   | 10.64.15.1 – 10.64.15.62     |
| A3     | 10.64.15.64    | 255.255.255.192 | 10.64.15.127  | 10.64.15.65 – 10.64.15.126   |
| A2     | 10.64.15.128   | 255.255.255.224 | 10.64.15.159  | 10.64.15.129 – 10.64.15.158  |
| A8     | 10.64.15.160   | 255.255.255.240 | 10.64.15.175  | 10.64.15.161 – 10.64.15.174  |
| A4     | 10.64.15.176   | 255.255.255.248 | 10.64.15.183  | 10.64.15.177 – 10.64.15.182  |
| A14    | 10.64.15.184   | 255.255.255.248 | 10.64.15.191  | 10.64.15.185 – 10.64.15.190  |
| A15    | 10.64.15.192   | 255.255.255.248 | 10.64.15.199  | 10.64.15.193 – 10.64.15.198  |
| A7     | 10.64.15.200   | 255.255.255.252 | 10.64.15.203  | 10.64.15.201 – 10.64.15.202  |
| A16    | 10.64.15.204   | 255.255.255.252 | 10.64.15.207  | 10.64.15.205 – 10.64.15.206  |
| A17    | 10.64.15.208   | 255.255.255.252 | 10.64.15.211  | 10.64.15.209 – 10.64.15.210  |
| A18    | 10.64.15.212   | 255.255.255.252 | 10.64.15.215  | 10.64.15.213 – 10.64.15.214  |
| A19    | 10.64.15.216   | 255.255.255.252 | 10.64.15.219  | 10.64.15.217 – 10.64.15.218  |
| A20    | 10.64.15.220   | 255.255.255.252 | 10.64.15.223  | 10.64.15.221 – 10.64.15.222  |
| A21    | 10.64.15.224   | 255.255.255.252 | 10.64.15.227  | 10.64.15.225 – 10.64.15.226  |
| A22    | 10.64.15.228   | 255.255.255.252 | 10.64.15.231  | 10.64.15.229 – 10.64.15.230  |
| A23    | 10.64.15.232   | 255.255.255.252 | 10.64.15.235  | 10.64.15.233 – 10.64.15.234  |


### Tree VLSM
<img width="22024" height="6902" alt="Vlsm-Praktikum" src="https://github.com/user-attachments/assets/ae3293b8-d87e-472f-8fe0-1342f5394415" />

### Config VLSM

## AMONSUL (ROUTER PUSAT)

```
# A7 - to Fornost
auto eth0
iface eth0 inet static
    address 10.64.15.202
    netmask 255.255.255.252
    gateway 10.64.15.201

# A18 - to Minastir
auto eth1
iface eth1 inet static
    address 10.64.15.213
    netmask 255.255.255.252

# A19 - to Eregion
auto eth2
iface eth2 inet static
    address 10.64.15.217
    netmask 255.255.255.252

# A17 - to NAT1
auto eth3
iface eth3 inet static
    address 10.64.15.210
    netmask 255.255.255.252

# Default route to NAT
post-up route add default gw 10.64.15.209

# Route to A6 (Fornost side)
post-up route add -net 10.64.14.0 netmask 255.255.255.128 gw 10.64.15.201

# Route to A15, A14, A13 (via Minastir)
post-up route add -net 10.64.15.193 netmask 255.255.255.248 gw 10.64.15.214
post-up route add -net 10.64.15.185 netmask 255.255.255.248 gw 10.64.15.214
post-up route add -net 10.64.15.1   netmask 255.255.255.192 gw 10.64.15.214

# Route to A12, A5, A8, A3, A2 via Eregion
post-up route add -net 10.64.4.0 netmask 255.255.252.0 gw 10.64.15.218
post-up route add -net 10.64.14.128 netmask 255.255.255.128 gw 10.64.15.218
post-up route add -net 10.64.15.64  netmask 255.255.255.192 gw 10.64.15.218
post-up route add -net 10.64.15.128 netmask 255.255.255.224 gw 10.64.15.218
post-up route add -net 10.64.12.0   netmask 255.255.254.0   gw 10.64.15.218

```
## Minastir

```
# A18 - to Amonsul
auto eth0
iface eth0 inet static
    address 10.64.15.214
    netmask 255.255.255.252
    gateway 10.64.15.213

# A16 - to Anor
auto eth1
iface eth1 inet static
    address 10.64.15.205
    netmask 255.255.255.252

# A6 - LAN
auto eth2
iface eth2 inet static
    address 10.64.14.1
    netmask 255.255.255.128

post-up route add default gw 10.64.15.213
post-up route add -net 10.64.15.192 netmask 255.255.255.248 gw 10.64.15.206  # A15
post-up route add -net 10.64.15.160 netmask 255.255.255.240 gw 10.64.15.206  # A11

```

## Anor
```
auto eth0
iface eth0 inet static
    address 10.64.15.206
    netmask 255.255.255.252
    gateway 10.64.15.205

auto eth1
iface eth1 inet static
    address 10.64.4.1
    netmask 255.255.252.0

auto eth2
iface eth2 inet static
    address 10.64.15.193
    netmask 255.255.255.248

post-up route add default gw 10.64.15.205
post-up route add -net 10.64.15.184 netmask 255.255.255.248 gw 10.64.15.194 # A14
post-up route add -net 10.64.15.1   netmask 255.255.255.192 gw 10.64.15.194 # A13
```

## Eregion
```
auto eth0
iface eth0 inet static
    address 10.64.15.218
    netmask 255.255.255.252
    gateway 10.64.15.217

auto eth1
iface eth1 inet static
    address 10.64.15.221
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.64.14.129
    netmask 255.255.255.128

post-up route add default gw 10.64.15.217

post-up route add -net 10.64.15.128 netmask 255.255.255.224 gw 10.64.15.222  # A2
post-up route add -net 10.64.15.64  netmask 255.255.255.192 gw 10.64.15.222  # A3
post-up route add -net 10.64.12.0   netmask 255.255.254.0   gw 10.64.15.222  # A1
post-up route add -net 10.64.15.161 netmask 255.255.255.240 gw 10.64.15.222  # A8

```

## NUMENOR
```
auto eth0
iface eth0 inet static
    address 10.64.15.222
    netmask 255.255.255.252
    gateway 10.64.15.221

auto eth1
iface eth1 inet static
    address 10.64.15.225
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.64.15.229
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.64.15.233
    netmask 255.255.255.252

# A9 LAN
auto eth4
iface eth4 inet static
    address 10.64.0.1
    netmask 255.255.252.0

post-up route add default gw 10.64.15.221

```

## Gudur
```
auto eth0
iface eth0 inet static
    address 10.64.15.226
    netmask 255.255.255.252
    gateway 10.64.15.225

auto eth1
iface eth1 inet static
    address 10.64.14.129
    netmask 255.255.255.128


```

## Mordor
```
auto eth0
iface eth0 inet static
    address 10.64.15.230
    netmask 255.255.255.252
    gateway 10.64.15.229

```

## Erain
```
auto eth0
iface eth0 inet static
    address 10.64.15.234
    netmask 255.255.255.252
    gateway 10.64.15.233

```

## Valinor
```
auto eth0
iface eth0 inet static
    address 10.64.15.177
    netmask 255.255.255.248

auto eth1
iface eth1 inet static
    address 10.64.12.1
    netmask 255.255.254.0

```

## Valmar
```
auto eth0
iface eth0 inet static
    address 10.64.15.129
    netmask 255.255.255.224

auto eth1
iface eth1 inet static
    address 10.64.15.65
    netmask 255.255.255.192

auto eth2
iface eth2 inet static
    address 10.64.14.129
    netmask 255.255.255.128

```

## Shadow 
```
auto eth0
iface eth0 inet static
    address 10.64.12.2
    netmask 255.255.254.0
    gateway 10.64.12.1

```

## Anarion
```
auto eth0
iface eth0 inet static
    address 10.64.12.3
    netmask 255.255.254.0
    gateway 10.64.12.1

```

## Lindon
```
auto eth0
iface eth0 inet static
    address 10.64.12.4
    netmask 255.255.254.0
    gateway 10.64.12.1

```

## Fornost
```
auto eth0
iface eth0 inet static
    address 10.64.14.2
    netmask 255.255.255.128
    gateway 10.64.14.1

auto eth1
iface eth1 inet static
    address 10.64.15.201
    netmask 255.255.255.252

```

## Morgoth 
```
auto eth0
iface eth0 inet static
    address 10.64.15.185
    netmask 255.255.255.248

```

## Throne
```
auto eth0
iface eth0 inet static
    address 10.64.15.193
    netmask 255.255.255.248

auto eth1
iface eth1 inet static
    address 10.64.15.185
    netmask 255.255.255.248

```
