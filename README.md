# QATesterTlab

## Mind Map Fitur Software 

### Sistem Monitoring Lingkungan

## Sub Sistem Perangkat IoT
- **Sensor Lingkungan**
  - Suhu Lingkungan
  - Kelembaban Lingkungan
  - Intensitas Cahaya Lingkungan
  - Gambar Lingkungan
- **Mengisi Daya dari Solar Panel**

## Sub Sistem Komunikasi
- Modem 4G untuk Mengirim Data Sensor
- Protokol MQTT/HTTP
- Perintah dari Back End untuk Aktifkan Sensor

## Sub Sistem Back End
- **Menerima dan Menyimpan Data Sensor**
  - Suhu Lingkungan
  - Kelembaban Lingkungan
  - Intensitas Cahaya Lingkungan
  - Gambar Perangkat
- Menyimpan Data ke Postgres
- Menyimpan Gambar ke Object Storage
- Mengolah Data untuk Front End

## Sub Sistem Front End
- Menampilkan Data Sensor
- Grafik Data Sensor Berdasarkan Waktu dan Lokasi
- Notifikasi Status Perangkat
- Mengirim Perintah ke Sub Sistem Back End
- Mengatur Jadwal Kirim Data
- Mengelola Koleksi Foto Serangga
- Hak Akses (RBAC)


---

## User Story dan Acceptance Criteria

### EPIC 1: Sub Sistem Perangkat IoT

#### User Story 1:
Sebagai pengguna, saya ingin perangkat IoT dapat mendeteksi suhu lingkungan sehingga saya bisa memantau kondisi suhu di lingkungan tertentu.

**Acceptance Criteria:**
- Perangkat IoT harus mampu membaca suhu lingkungan secara real-time.
- Sistem harus menyimpan data suhu untuk periode tertentu.
- Perangkat mampu mengirim data suhu ke subsistem komunikasi.

#### User Story 2:
Sebagai pengguna, saya ingin perangkat IoT mengambil gambar lingkungan sehingga saya bisa memantau kondisi visual.

**Acceptance Criteria:**
- Perangkat harus dapat mengambil gambar lingkungan dalam interval tertentu.
- Gambar harus dikirim ke subsistem komunikasi dan disimpan di back end.

---

### EPIC 2: Sub Sistem Komunikasi

#### User Story 1:
Sebagai pengguna, saya ingin data sensor suhu dikirimkan dari perangkat IoT ke server melalui modem 4G.

**Acceptance Criteria:**
- Data sensor suhu berhasil dikirim menggunakan modem 4G.
- Pengiriman data menggunakan protokol MQTT atau HTTP sesuai konfigurasi.
- Jika pengiriman gagal, sistem mencoba ulang setelah waktu tertentu.

#### User Story 2:
Sebagai pengguna, saya ingin dapat mengirim perintah dari backend untuk mengaktifkan sensor pada perangkat IoT.

**Acceptance Criteria:**
- Backend dapat mengirim perintah aktivasi sensor melalui MQTT/HTTP.
- Perangkat IoT harus mengeksekusi perintah aktivasi sensor dengan respon konfirmasi berhasil/tidaknya.

---

### EPIC 3: Sub Sistem Back End

#### User Story 1:
Sebagai pengguna, saya ingin backend menyimpan data sensor suhu, kelembaban, dan intensitas cahaya ke database untuk analisis lebih lanjut.

**Acceptance Criteria:**
- Sistem dapat menyimpan data dari sensor suhu, kelembaban, dan intensitas cahaya ke Postgres.
- Data disimpan dengan metadata seperti timestamp dan ID perangkat.

#### User Story 2:
Sebagai pengguna, saya ingin backend menyimpan gambar ke Object Storage sehingga gambar dapat diakses melalui front end.

**Acceptance Criteria:**
- Gambar yang dikirim dari perangkat IoT berhasil disimpan di Object Storage.
- Gambar dapat diakses dan dilihat dari front end.

---

### EPIC 4: Sub Sistem Front End

#### User Story 1:
Sebagai pengguna, saya ingin melihat grafik hasil pengukuran sensor lingkungan berdasarkan filter waktu dan lokasi.

**Acceptance Criteria:**
- Front end harus menampilkan grafik data suhu, kelembaban, dan intensitas cahaya berdasarkan filter waktu (jam, harian, mingguan).
- Pengguna dapat memfilter data berdasarkan lokasi perangkat IoT.

#### User Story 2:
Sebagai pengguna, saya ingin mendapatkan notifikasi jika ada data baru yang masuk dari perangkat IoT atau perangkat non-aktif.

**Acceptance Criteria:**
- Sistem mengirimkan notifikasi saat ada data baru dari perangkat IoT.
- Sistem mengirimkan notifikasi ketika perangkat IoT berada dalam kondisi tidak aktif.

---

## Test Case dengan Format Gherkin

### Test Case 1: Mendeteksi Suhu Lingkungan
```
Feature: Deteksi Suhu Lingkungan
  As a user
  I want the IoT device to detect environmental temperature
  So that I can monitor the temperature remotely

Scenario: IoT device detects temperature
  Given the IoT device is powered on
  When the environment has a measurable temperature
  Then the system should detect and log the temperature data
  And the temperature data should be sent to the communication subsystem
```
### Test Case 2: Mengirim Data Suhu ke Backend
```
Feature: Mengirim Data Suhu ke Backend
  As a user
  I want the IoT device to send temperature data to the backend system
  So that the backend system can store and process the data

Scenario: Sending temperature data to backend
  Given the IoT device has temperature data
  When the device attempts to send data via 4G modem
  Then the data should be sent using MQTT or HTTP
  And the backend should receive and store the data in Postgres
```
###Test Case 3: Menampilkan Data Suhu di Front End
```
Feature: Menampilkan Data Suhu di Front End
  As a user
  I want to see the temperature data displayed on the frontend
  So that I can easily monitor the environment

Scenario: Displaying temperature data on frontend
  Given the backend has stored temperature data
  When the user accesses the frontend
  Then the temperature data should be displayed in a graph
  And the user should be able to filter data by time and location


