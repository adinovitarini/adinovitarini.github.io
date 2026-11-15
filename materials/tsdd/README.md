# Teknik Sistem dan Digital Dasar

Starter situs kuliah Sphinx dengan tema Read the Docs. Isi situs berada di folder `docs/` dan dapat diedit dalam Markdown. Tambahkan halaman ke daftar `toctree` di `docs/index.md` agar muncul di navigasi.

## Pratinjau lokal

Gunakan Python 3.11 atau 3.12 dan jalankan perintah berikut dari folder ini.

```sh
python -m pip install -r requirements.txt
python -m sphinx -W -b html docs _build/html
python -m http.server --bind 127.0.0.1 --directory _build/html 8000
```

Buka http://127.0.0.1:8000. Untuk menaruh sumber di GitHub, buat repo dan unggah isi folder ini. Folder `_build/` berisi keluaran lokal dan diabaikan oleh Git.
