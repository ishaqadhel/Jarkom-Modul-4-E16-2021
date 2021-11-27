# 📖 Laporan Resmi Jaringan Komputer Modul 4 E16 2021 

**Anggota Kelompok:**
 - Ishaq Adheltyo (05111940000167)

## 📝 Soal
![image](https://user-images.githubusercontent.com/49280352/143672114-e7b6fdd9-9556-4d8c-9e94-df6a207df35e.png)
![image](https://user-images.githubusercontent.com/49280352/143672139-b98e669a-2004-4a0f-976f-a9435dd12848.png)

## 📡 Pembagian Region
![image](https://user-images.githubusercontent.com/49280352/143672252-68c08541-69be-47d7-81ad-617cb7c5df82.png)

## 📶 Table Subnet
![image](https://user-images.githubusercontent.com/49280352/143672295-d287727c-f13b-49cf-93a4-86f49b2661a1.png)

## 📡 VSLM

### 🗒️ Pengertian
Teknik VSLM untuk mengefisienkan pembagian IP di dalam jaringan. Besar netmask disesuaikan dengan banyaknya komputer/ host yang membutuhkan alamat IP.

### 📖 List IP Host
![image](https://user-images.githubusercontent.com/49280352/143672686-8bd43667-f8a9-4c7d-bae1-2760c4a1db7c.png)

Dapat dilihat di tabel diatas bahwa total jumlah ip yang dibutuhkan oleh seluruh pada host adalah 5841 yang dimana masuk kategori netmask 19. Oleh karena itu, untuk pembagian IP pada pohon dimulai dengan netmask 19.

### 🌳 Pohon Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/143672873-1e50ef6e-8616-478a-aba3-f588f660c8ba.png)

**Penjelasan Penambahan IP:**

Q: Mengapa 10.37.0.0/20 dilanjutkan dengan 10.37.16.0/20 ?

A: 
- IPv4 terdiri dari 32 bit dengan 8 bit di setiap titiknya {(x.x.x.x) x berisi 8bit}.
- Digunakan Rumus x = (32 - length netmask) MOD 8
- x = (32 - 20) MOD 8
- x = 4
- Kemudian hasil x gunakan dirumus 2^x untuk mencari network address berikutnya
- 2^4 = 16
- Berarti setelah 10.37.0.0/20 dilanjut dengan 10.37.16.0/20

Untuk lebih mudahnya bisa menggunakan calculator pada https://www.calculator.net/ip-subnet-calculator.html

### 📚 Hasil Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/143673284-d9ee3a7a-4889-4184-9602-8ab959f268d8.png)

### ⚖️ Routing
![image](https://user-images.githubusercontent.com/49280352/143673900-75f8a938-287d-49d5-a57a-a6a07b82289c.png)
![image](https://user-images.githubusercontent.com/49280352/143673915-3691163d-2b84-41ac-8add-2474ececa313.png)

### 👨‍💻 Screenshot CPT
![image](https://user-images.githubusercontent.com/49280352/143673996-5354524c-5ab9-46ab-98bc-e72d344af496.png)

## 📡 CIDR

### 🗒️ Pengertian
Teknik CIDR juga didasarkan pada jumlah komputer/ host yang ada di dalam subnet. Tetapi cara mendapatkan subnet besar tidak sama dengan VLSM.

### 📖 Penentuan Level Topologi
![image](https://user-images.githubusercontent.com/49280352/143674143-67748331-4965-4e95-ac71-1073a5fbdaea.png)

### 🪜 Pembagian Level Topologi (Nama Region Cek di Pembagian Region)
![image](https://user-images.githubusercontent.com/49280352/143674385-7c756fb7-3e57-4599-a6a1-183f0f53ea97.png)

**Cara Menyatukan Subnet:**
- Ambil dari level subnet paling bawah
- Satukan maksimal 2 bagian, ambil netmask paling tinggi kemudian tambah 1

### 🌳 Pohon Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/143674657-3346d8dc-d1b3-4e01-8f8e-a7dbecba39ee.png)

**Cara Pembagian Turunan Level**
- Berbeda dengan VLSM, untuk CIDR lihat cara pembentukan sebuah Netmask. Misal 15 dibentuk dengan netmask /16 dan /21 maka dari /15 turun menjadi /16 dan /21.

**Mengapa Prefix Berubah?**
- Karena level paling tinggi didapatkan dengan level netmask 15, setelah di cek di IP calculator untuk IP 10.37.*.* tidak menjadi network address melainkan masuk di range network address 10.36.*.* /15

**Cara menentukan urutan ip dari cabang (kiri ke kanan):**
- Q: Mengapa 10.37.0.0 /22 kanannya menjadi 10.37.4.0 /30 ?
- A: Karena 10.37.0.0 /22 network address selanjutnya sesuai perhitungan adalah 10.37.4.0 /22. Ambil 10.37.4.0 untuk network address tetapi dengan netmask 30 (sesuai node)

### 📚 Hasil Pembagian IP
![image](https://user-images.githubusercontent.com/49280352/143674875-1a64d2d6-57d1-4899-82c9-83b14fb484ba.png)
![image](https://user-images.githubusercontent.com/49280352/143674881-32593835-9489-4e94-89ff-bac5919ebdce.png)

### ⚖️ Config Routing di GNS3

#### 🔧 Foosha

```
route add -net 10.36.32.0 netmask 255.255.252.0 gw 10.36.64.1
route add -net 10.36.8.0 netmask 255.255.255.128 gw 10.36.64.1
route add -net 10.36.0.0 netmask 255.255.248.0 gw 10.36.64.1
route add -net 10.36.16.0 netmask 255.255.255.252 gw 10.36.64.1
route add -net 10.36.164.0 netmask 255.255.252.0 gw 10.36.192.2
route add -net 10.36.162.0 netmask 255.255.255.240 gw 10.36.192.2
route add -net 10.36.160.0 netmask 255.255.254.0 gw 10.36.192.2
route add -net 10.36.136.0 netmask 255.255.255.252 gw 10.36.192.2
route add -net 10.36.128.0 netmask 255.255.252.0 gw 10.36.192.2
route add -net 10.36.132.0 netmask 255.255.255.0 gw 10.36.192.2
route add -net 10.36.144.0 netmask 255.255.255.252 gw 10.36.192.2
```

#### 🔧 Water7

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.64.2
route add -net 10.36.8.0 netmask 255.255.255.128 gw 10.36.16.1
route add -net 10.36.0.0 netmask 255.255.248.0 gw 10.36.16.1
route add -net 10.36.16.0 netmask 255.255.255.252 gw 10.36.16.1
```

#### 🔧 Pucci

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.16.2
```

#### 🔧 Guanhao

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.192.1
route add -net 10.36.132.0 netmask 255.255.255.0 gw 10.36.144.2
route add -net 10.36.128.0 netmask 255.255.252.0 gw 10.36.144.2
route add -net 10.36.136.0 netmask 255.255.255.252 gw 10.36.144.2
route add -net 10.36.162.0 netmask 255.255.255.240 gw 10.36.160.2
route add -net 10.36.144.0 netmask 255.255.255.252 gw 10.36.144.2
```

#### 🔧 Oimo

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.144.1
route add -net 10.36.128.0 netmask 255.255.252.0 gw 10.36.132.2
```

#### 🔧 Seastone

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.132.1
```

#### 🔧 Alabasta

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.36.160.1
```

### 🔧 Config Node

#### 🔧 Edit Network Configuration Jipangu

```
auto eth0
iface eth0 inet static
address 10.36.8.2
netmask 255.255.255.128
gateway 10.36.8.1
```

#### 🔧 Edit Network Configuration Pucci

```
auto eth0
iface eth0 inet static
address 10.36.16.1
netmask 255.255.255.252
gateway 10.36.16.2

auto eth1
iface eth1 inet static
address 10.36.8.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 10.36.0.1
netmask 255.255.248.0
```


#### 🔧 Edit Network Configuration Courtyard

```
auto eth0
iface eth0 inet static
address 10.36.0.2
netmask 255.255.248.0
gateway 10.36.0.1
```

#### 🔧 Edit Network Configuration Calmbelt

```
auto eth0
iface eth0 inet static
address 10.36.64.1
netmask 255.255.255.252
gateway 10.36.64.2

auto eth1
iface eth1 inet static
address 10.36.32.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 10.36.16.2
netmask 255.255.255.252
```

#### 🔧 Edit Network Configuration Cipher

```
auto eth0
iface eth0 inet static
address 10.36.32.2
netmask 255.255.252.0
gateway 10.36.32.1
```

#### 🔧 Edit Network Configuration Foosha

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.37.0.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 10.36.64.2
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 10.36.192.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.37.4.1
netmask 255.255.255.252
```

#### 🔧 Edit Network Configuration Blueno

```
auto eth0
iface eth0 inet static
address 10.37.0.2
netmask 255.255.252.0
gateway 10.37.0.1
```

#### 🔧 Edit Network Configuration Doriki

```
auto eth0
iface eth0 inet static
address 10.37.4.2
netmask 255.255.255.252
gateway 10.37.4.1
```

#### 🔧 Edit Network Configuration Guanhao

```
auto eth0
iface eth0 inet static
address 10.36.192.2
netmask 255.255.255.252
gateway 10.36.192.1

auto eth1
iface eth1 inet static
address 10.36.164.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 10.36.160.1
netmask 255.255.254.0


auto eth3
iface eth3 inet static
address 10.36.144.1
netmask 255.255.255.252
```

#### 🔧 Edit Network Configuration Jabra

```
auto eth0
iface eth0 inet static
address 10.36.164.2
netmask 255.255.252.0
gateway 10.36.164.1
```

#### 🔧 Edit Network Configuration Maingate

```
auto eth0
iface eth0 inet static
address 10.36.160.3
netmask 255.255.254.0
gateway 10.36.160.1
```

#### 🔧 Edit Network Configuration Alabasta

```
auto eth0
iface eth0 inet static
address 10.36.160.2
netmask 255.255.254.0
gateway 10.36.160.1

auto eth1
iface eth1 inet static
address 10.36.162.1
netmask 255.255.255.240
```

#### 🔧 Edit Network Configuration Jorge

```
auto eth0
iface eth0 inet static
address 10.36.162.2
netmask 255.255.255.240
gateway 10.36.162.1
```

#### 🔧 Edit Network Configuration Oimo

```
auto eth0
iface eth0 inet static
address 10.36.144.2
netmask 255.255.255.252
gateway 10.36.144.1

auto eth1
iface eth1 inet static
address 10.36.132.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.36.136.1
netmask 255.255.255.252
```

#### 🔧 Edit Network Configuration EniesLobby

```
auto eth0
iface eth0 inet static
address 10.36.132.3
netmask 255.255.255.0
gateway 10.36.132.1
```

#### 🔧 Edit Network Configuration Seastone

```
auto eth0
iface eth0 inet static
address 10.36.132.2
netmask 255.255.255.0
gateway 10.36.132.1

auto eth1
iface eth1 inet static
address 10.36.128.1
netmask 255.255.252.0
```

#### 🔧 Edit Network Configuration Elena

```
auto eth0
iface eth0 inet static
address 10.36.128.2
netmask 255.255.252.0
gateway 10.36.128.1
```

#### 🔧 Edit Network Configuration Fukurou

```
auto eth0
iface eth0 inet static
address 10.36.136.2
netmask 255.255.252.0
gateway 10.36.136.1
```

### 👨‍💻 Screenshot GNS3
![image](https://user-images.githubusercontent.com/49280352/143675184-9802fcf8-9ff4-471f-9c09-9dbbbb5db0aa.png)

## 🧗 Kendala
- Penjelasan yang ada pada modul kurang jelas dan tidak lengkap
