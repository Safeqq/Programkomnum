# Newton-Gregory Backward Derivative (Python Implementation)

Proyek ini merupakan implementasi metode **Newton-Gregory Backward** untuk menghitung **turunan pertama** dari data numerik diskrit. Program ini menggunakan pendekatan selisih mundur (backward differences) dan sangat cocok jika nilai \( x \) yang ingin dihitung lebih dekat ke **ujung kanan** dari dataset.

---

## 🔧 Tujuan Program

Menghitung turunan numerik \( f'(x) \) berdasarkan data titik-titik \( (x_i, y_i) \) yang diketahui, menggunakan pendekatan backward difference hingga derajat ke-4.

---

## 🧠 Penjelasan Kode

### 1. `build_backward_deltaerence_table(nilai_X, nilai_Y)`

- Fungsi ini membangun tabel selisih mundur (backward difference table).
- Data \( X \) dan \( Y \) diurutkan dari kanan ke kiri.
- Selisih pertama dihitung sebagai:
  \[
  \Delta y_i = y_i - y_{i+1}
  \]
- Setiap baris baru pada tabel adalah selisih dari baris sebelumnya.

---

### 2. `extract_deltas_at_x0(x_st, table, x0)`

- Fungsi ini mengambil nilai-nilai selisih (Δy, Δ²y, dst.) dari posisi yang sesuai dengan titik \( x_0 \).
- Ini digunakan untuk membentuk turunan berdasarkan posisi \( x_0 \) pada tabel backward.

---

### 3. `derivative_ng_backward_verbose(nilai_X, nilai_Y, x0, x)`

Fungsi utama yang:
- Menghitung jarak antar titik: `h = nilai_X[1] - nilai_X[0]`
- Menghitung parameter \( s = \frac{x - x_0}{h} \)
- Mengambil semua nilai delta dari tabel selisih mundur
- Menghitung setiap bagian turunan menggunakan formula:

\[
f'(x) = \frac{1}{h} \left[
  \Delta y +
  \frac{(2s+1)}{2} \Delta^2 y +
  \frac{(3s^2 + 6s + 2)}{6} \Delta^3 y +
  \frac{(4s^3 + 18s^2 + 22s + 6)}{24} \Delta^4 y
\right]
\]

- Fungsi juga mencetak penjelasan langkah demi langkah (verbose), termasuk nilai koefisien dan hasil antara dari setiap komponen turunan.

---

## 📌 Contoh Data & Penggunaan

```python
nilai_X = [2, 4, 6, 8, 10, 12, 14, 16, 18]
nilai_Y = [-940, -6008, -11652, 1040, 74020, 279960, 729932, 1581088, 3044340]

x0 = 10
x = 11

result = derivative_ng_backward_verbose(nilai_X, nilai_Y, x0, x)
print(f"\nHasil akhir turunan f'({x}) ≈ {result}")`
