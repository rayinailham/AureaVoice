# AureaVoice - AI Accent Analyzer

AureaVoice adalah sebuah aplikasi web yang dirancang untuk menganalisis aksen bicara pengguna secara *real-time*. Aplikasi ini mampu merekam suara pengguna melalui mikrofon dan memberikan skor kepercayaan (confidence score) mengenai seberapa mirip aksen tersebut dengan aksen standar Amerika (US Accent).

Proyek ini dibangun dengan arsitektur client-server modern, memisahkan antarmuka pengguna (frontend) dari logika pemrosesan AI (backend) untuk skalabilitas dan kemudahan pengembangan.

## ✨ Fitur Utama

- **Perekaman Audio**: Merekam audio langsung dari browser pengguna.
- **Analisis Aksen**: Menggunakan model AI canggih (SpeechBrain) untuk menganalisis dan memberikan skor pada aksen Amerika.
- **Antarmuka Responsif**: Desain yang bersih dan mudah digunakan pada berbagai perangkat.
- **Kontainerisasi Docker**: Siap untuk dijalankan dan didistribusikan dengan mudah menggunakan Docker dan Docker Compose.

---

## 🛠️ Tumpukan Teknologi (Tech Stack)

Aplikasi ini terdiri dari dua komponen utama:

#### 🎤 Frontend (`av-frontend`)
- **Framework**: Vanilla JavaScript (ES6 Modules)
- **Build Tool**: Vite
- **Web Server (Produksi)**: Nginx (di dalam kontainer Docker)
- **Styling**: CSS Murni

#### 🧠 Backend (`av-backend`)
- **Framework**: FastAPI (Python)
- **Server**: Uvicorn
- **AI/ML**: SpeechBrain, PyTorch, Hugging Face
- **Bahasa**: Python 3.10

---

## 🚀 Menjalankan Aplikasi dengan Docker (Cara Rekomendasi)

Cara termudah dan tercepat untuk menjalankan AureaVoice adalah dengan menggunakan Docker. Anda tidak perlu menginstall Python, Node.js, atau dependensi lainnya secara manual.

### Prasyarat
- **Git**: [Install Git](https://git-scm.com/downloads)
- **Docker & Docker Compose**: [Install Docker Desktop](https://www.docker.com/products/docker-desktop/) (sudah termasuk Docker Compose)

### Langkah-langkah Instalasi

1.  **Clone Repositori**
    Buka terminal atau Command Prompt dan jalankan perintah berikut:
    ```sh
    git clone <URL_REPOSITORI_GITHUB_ANDA>
    ```

2.  **Masuk ke Direktori Proyek**
    ```sh
    cd AureaVoice
    ```

3.  **Jalankan dengan Docker Compose**
    Perintah ini akan secara otomatis membangun *image* untuk frontend dan backend, mengunduh semua dependensi (termasuk model AI), dan menjalankan kedua layanan.
    ```sh
    docker-compose up --build
    ```
    > **Catatan:** Proses `build` pertama kali mungkin akan memakan waktu cukup lama karena perlu mengunduh base image dan model AI yang cukup besar. Proses selanjutnya akan jauh lebih cepat.

4.  **Akses Aplikasi**
    Setelah proses selesai dan Anda melihat log dari `aureavoice-backend` dan `aureavoice-frontend` berjalan di terminal, buka browser Anda dan akses:
    > **[http://localhost:5173](http://localhost:5173)**

Aplikasi AureaVoice sekarang siap untuk digunakan!

### Menghentikan Aplikasi
Untuk menghentikan semua layanan, tekan `Ctrl + C` di terminal tempat `docker-compose` berjalan. Untuk menghapus kontainer, jalankan:
```sh
docker-compose down
```

---

## 🔧 Pengembangan Lokal (Tanpa Docker)

Jika Anda ingin mengembangkan atau memodifikasi kode, Anda bisa menjalankan setiap layanan secara terpisah.

### Menjalankan Backend
1.  Masuk ke direktori backend: `cd av-backend`
2.  Buat dan aktifkan virtual environment:
    ```sh
    python -m venv .venv
    # Windows
    .\.venv\Scripts\activate
    # macOS/Linux
    source .venv/bin/activate
    ```
3.  Install dependensi: `pip install -r requirements.txt`
4.  Jalankan server FastAPI: `uvicorn main:app --reload`
5.  Backend akan berjalan di `http://localhost:8000`.

### Menjalankan Frontend
1.  Masuk ke direktori frontend: `cd av-frontend`
2.  Install dependensi: `npm install`
3.  Jalankan server development Vite: `npm run dev`
4.  Frontend akan berjalan di `http://localhost:5173`.

> **Penting:** Pastikan backend sudah berjalan sebelum menggunakan fungsionalitas pada frontend.

---

## 📂 Struktur Proyek

```
AureaVoice/
├── av-backend/         # Direktori untuk Backend (Python, FastAPI)
│   ├── main.py
│   ├── requirements.txt
│   └── Dockerfile
├── av-frontend/        # Direktori untuk Frontend (JavaScript, Vite)
│   ├── src/
│   ├── index.html
│   ├── package.json
│   └── Dockerfile
├── docker-compose.yml  # File utama untuk orkestrasi Docker
└── README.md           # File ini
```
