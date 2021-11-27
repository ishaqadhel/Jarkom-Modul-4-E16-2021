# 📖 Laporan Resmi Jaringan Komputer Modul 3 E16 2021 

**Anggota Kelompok:**
 - Ishaq Adheltyo (05111940000167)

## 📝 Soal
![image](https://user-images.githubusercontent.com/49280352/143672114-e7b6fdd9-9556-4d8c-9e94-df6a207df35e.png)
![image](https://user-images.githubusercontent.com/49280352/143672139-b98e669a-2004-4a0f-976f-a9435dd12848.png)

## 📡 Pembagian Region
![image](https://user-images.githubusercontent.com/49280352/143672252-68c08541-69be-47d7-81ad-617cb7c5df82.png)
![image](https://user-images.githubusercontent.com/49280352/143673943-3f705a2d-a88f-4eea-b6c2-caafbf31399c.png)


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
