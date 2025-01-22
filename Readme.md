# Penjelasan Topologi

1. **Router 1**:

   - **AS Number**: 65001
   - **IP Address**:
     - ether1: `172.16.1.1/24` (koneksi ke Internet melalui Tunnel dengan IP Public `10.1.1.1/32`)
     - ether2: `10.10.10.1/24` (koneksi ke Router 2)
     - ether3: `14.14.14.1/24` (koneksi ke komputer lokal)

2. **Router 2**:

   - **AS Number**: 65002
   - **IP Address**:
     - ether1: `172.16.2.1/24` (koneksi ke Internet melalui Tunnel dengan IP Public `172.16.2.1/32`)
     - ether2: `10.10.10.2/24` (koneksi ke Router 1)
     - ether3: `192.168.100.1/24` (koneksi ke komputer lokal)
     - ether4: `192.168.101.1/24` (koneksi tambahan untuk pengembangan)

3. **Router 3**:
   - **AS Number**: 65003
   - **IP Address**:
     - ether1: `10.10.30.1/24` (koneksi ke Router 2)
     - ether2: `192.168.102.1/24` (koneksi ke komputer lokal)
     - ether3: `192.168.103.1/24` (koneksi tambahan untuk pengembangan)

---

### **Koneksi Antar Router**

1. **Router 1 ke Router 2**:

   - IP subnet: `10.10.10.0/24`
   - Router 1: `10.10.10.1`
   - Router 2: `10.10.10.2`

2. **Router 2 ke Router 3**:
   - IP subnet: `10.10.30.0/24`
   - Router 2: `10.10.30.1`
   - Router 3: `10.10.30.2`

---

### **Koneksi ke Internet**

Setiap router memiliki koneksi ke Internet melalui Tunnel yang menggunakan IP Public:

- **Router 1**: `10.1.1.1/32`
- **Router 2**: `172.16.2.1/32`
- **Router 3**: `192.168.103.1/32`

---

### **Komputer Lokal**

1. **Komputer 1 (Router 1)**:

   - IP Subnet: `14.14.14.0/24`
   - Gateway: `14.14.14.1`

2. **Komputer 2 (Router 2)**:

   - IP Subnet: `192.168.100.0/24`
   - Gateway: `192.168.100.1`

3. **Komputer 3 (Router 3)**:
   - IP Subnet: `192.168.102.0/24`
   - Gateway: `192.168.102.1`

---

### **Konfigurasi BGP**

1. **Router 1**:

   - **AS Number**: 65001
   - **Neighbor Peers**:
     - Router 2: `10.10.10.2` (AS 65002)
   - **Advertised Networks**:
     - `172.16.1.0/24`
     - `10.10.10.0/24`
     - `14.14.14.0/24`

2. **Router 2**:

   - **AS Number**: 65002
   - **Neighbor Peers**:
     - Router 1: `10.10.10.1` (AS 65001)
     - Router 3: `10.10.30.2` (AS 65003)
   - **Advertised Networks**:
     - `172.16.2.0/24`
     - `10.10.10.0/24`
     - `10.10.30.0/24`
     - `192.168.100.0/24`

3. **Router 3**:
   - **AS Number**: 65003
   - **Neighbor Peers**:
     - Router 2: `10.10.30.1` (AS 65002)
   - **Advertised Networks**:
     - `10.10.30.0/24`
     - `192.168.102.0/24`

---

### **Fungsi dan Tujuan**

1. **Menggunakan BGP**:

   - Untuk memastikan konektivitas antara jaringan berbeda AS.
   - Untuk mempermudah routing antar subnet yang tersebar di jaringan yang berbeda.

2. **Koneksi Lokal dan Global**:
   - Komputer di masing-masing jaringan lokal dapat terhubung dengan Internet dan jaringan lain melalui router.

---

### **Ping dan Verifikasi**

1. **Ping antar Router**:

   - Pastikan semua router saling terhubung melalui IP masing-masing di subnet yang sama.

2. **Ping ke Internet**:

   - Pastikan masing-masing router dapat terhubung ke Internet melalui IP Publik.

3. **Ping dari Komputer ke Komputer**:
   - Pastikan komputer di setiap jaringan dapat saling terhubung.

---

### **Kesimpulan**

Topologi ini dirancang untuk mengimplementasikan protokol BGP dalam mengelola konektivitas antar jaringan yang tersebar di tiga router dengan tiga AS yang berbeda. Setiap router terhubung ke Internet dan dapat memberikan akses jaringan ke komputer lokal yang terhubung.
