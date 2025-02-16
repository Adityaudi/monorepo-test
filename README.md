# Deskripsi

Projek ini merupakan contoh penggunaan monorepo dengan dua aplikasi, yaitu web dan docs, yang di-deploy menggunakan Docker dan Docker Compose. Setiap aplikasi memiliki Dockerfile tersendiri dan dijalankan sebagai layanan terpisah dalam Docker Compose.

## Struktur Direktori
monorepo-test/ ├── apps/ │ ├── docs/ │ │ ├── _sidebar.md │ │ ├── index.html │ │ ├── Dockerfile │ │ └── ... │ └── web/ │ ├── public/ │ ├── src/ │ ├── Dockerfile │ └── ... ├── docker-compose.yml ├── package.json └── .next/
## Aplikasi

### Deskripsi Struktur

1. **Root Directory (monorepo-test/)**

    Anda berada di dalam direktori root yang berisi semua direktori dan file proyek utama. Berikut adalah beberapa file dan direktori penting yang ada di dalamnya:

    - **apps/**: Direktori ini berisi semua aplikasi atau modul yang ada di dalam proyek Anda. Misalnya, `web/` dan `docs/` adalah dua direktori yang akan dijelaskan di bawah ini.
    - **package.json**: File ini berisi informasi tentang modul dan dependencies yang diperlukan oleh proyek Anda.
    - **docker-compose.yml**: File ini berisi konfigurasi untuk Docker Compose, termasuk informasi tentang layanan yang ditentukan dan bagaimana mereka dijalankan.

2. **apps/** dan **subdirectories**

    - **apps/docs/**: Direktori ini berisi semua file yang diperlukan untuk aplikasi dokumen Anda. Selain itu, juga ada Dockerfile di dalam direktori ini.
    - **apps/web/**: Direktori ini berisi semua file yang diperlukan untuk aplikasi web Anda. Seperti yang telah disebutkan sebelumnya, juga ada Dockerfile di dalam direktori ini.

### Letak Dockerfile dan docker-compose.yml

- **Dockerfile** ada di dalam direktori `apps/docs/` dan `apps/web/`.
- **docker-compose.yml** ada di direktori root `monorepo-test/`.

## Cara Menjalankan Proyek 

### Langkah 1: Install Dependencies

1. Clone the project to your local machine using a tool like `git clone`.
2. Install pnpm and turbo (if not already installed) by running:
    ```bash
    npm install -g pnpm@latest && npm install -g turbo@latest
    ```
3. Install all project dependencies by running:
    ```bash
    pnpm install
    ```

### Langkah 2: Build and Run Docker containers

- Build the Docker image for all services defined in `docker-compose.yml` by running:
    ```bash
    docker-compose build
    ```

- Run the containers by executing:
    ```bash
    docker-compose up
    ```

### Mengakses Aplikasi

- Akses aplikasi web melalui browser: **[http://localhost:3000](http://localhost:3000)**
- Akses aplikasi docs melalui browser: **[http://localhost:3001](http://localhost:3001)**

**Nota:** Anda juga dapat menjalankan layanan Docker Compose untuk layanan tertentu saja. Misalnya jika hanya ingin menjalankan layanan web, gunakan berikut:
```bash
docker-compose up web