# Modul FSM · Alarm Level Bilga

Setelah modul ini, mahasiswa dapat menentukan state, menyusun aturan transisi, dan memeriksa keluaran dari urutan input. Contoh ini adalah model pembelajaran alarm.

## Definisi model

- `high` bernilai 1 ketika sensor mendeteksi level tinggi.
- `reset` bernilai 1 ketika operator meminta penghapusan alarm.
- State awal `NORMAL`. Keluaran `alarm` bernilai 1 selama state `ALARM`.
- Pada setiap langkah, model membaca kedua input, memperbarui state, lalu mencatat output.

| State saat ini | Kondisi | State berikutnya |
|---|---|---|
| NORMAL | high = 1 | ALARM |
| NORMAL | high = 0 | NORMAL |
| ALARM | high = 0 dan reset = 1 | NORMAL |
| ALARM | kondisi lainnya | ALARM |

## Simulasi

```python
def next_state(state, high, reset):
    if state == "NORMAL":
        return "ALARM" if high else "NORMAL"
    if not high and reset:
        return "NORMAL"
    return "ALARM"


state = "NORMAL"
inputs = [(0, 0), (1, 0), (1, 1), (0, 0), (0, 1)]

for step, (high, reset) in enumerate(inputs, start=1):
    state = next_state(state, high, reset)
    alarm = int(state == "ALARM")
    print(step, high, reset, state, alarm)
```

Urutan keluaran yang diharapkan adalah 0, 1, 1, 1, 0. Pada langkah ketiga, alarm bertahan karena sensor masih menunjukkan level tinggi. Pada langkah keempat, alarm bertahan karena belum ada permintaan reset.

## Latihan kelompok

1. Gambarkan FSM berdasarkan tabel, termasuk transisi yang mempertahankan state.
2. Tambahkan satu skenario ketika operator menekan reset bersamaan dengan deteksi level tinggi dari state awal. Tulis ekspektasi sebelum menjalankan simulasi.
3. Untuk sistem pilihan kelompok, definisikan input, output, dan state awal. Buat satu skenario normal dan satu kondisi batas. Laporkan perbandingan hasil aktual dengan ekspektasi.
