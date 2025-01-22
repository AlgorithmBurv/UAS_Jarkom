# Penjelasan Topologi Jaringan

## Komponen dan Koneksi

### Router

- **Router 1**

  - **Nomor AS**: 65001
  - **Interface**:
    - `ether1`: 172.16.1.1/24
    - `ether2`: 10.10.10.1/24
    - `ether3`: 14.14.14.1/24

- **Router 2**

  - **Nomor AS**: 65002
  - **Interface**:
    - `ether1`: 10.10.10.2/24
    - `ether2`: 192.168.2.1/24
    - `ether3`: 172.16.10.1/24

- **Router 3**
  - **Nomor AS**: 65003
  - **Interface**:
    - `ether1`: 10.10.10.3/24
    - `ether2`: 192.168.3.1/24
    - `ether3`: 192.10.10.1/24

### IP Publik dan Koneksi Internet

- **Koneksi Internet**
  - Router 1: IP Publik: `10.1.1.1/32`
  - Router 2: IP Publik: `172.16.1.1/32`
  - Router 3: IP Publik: `192.168.1.1/32`

## Fitur Utama Jaringan

- Topologi ini terdiri dari tiga sistem otonom (AS):

  - AS 65001 (Router 1)
  - AS 65002 (Router 2)
  - AS 65003 (Router 3)

- Koneksi antar-router:

  - **Router 1 ke Router 2** melalui `ether2`
  - **Router 2 ke Router 3** melalui `ether1`
  - **Router 1 ke Router 3** melalui `ether1`

- Setiap router terhubung langsung ke komputer lokal melalui `ether3`.

### Catatan:

- Konfigurasi ini mengasumsikan pengaturan protokol routing yang sesuai (misalnya, BGP) untuk memungkinkan komunikasi antar-sistem otonom.
- Koneksi ke internet publik memastikan setiap router memiliki aksesibilitas eksternal.
