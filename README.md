# Newton-Gregory Backward Derivative (Turunan Mundur)

Python ini digunakan untuk menghitung **turunan pertama** dari suatu fungsi menggunakan metode **Newton-Gregory Backward Difference**. Pendekatan ini berguna untuk melakukan estimasi turunan secara **numerik** dari data diskrit yang berada **dekat ujung kanan** tabel.

---

##  Tujuan
- Menghitung turunan pertama \( f'(x) \) dari sebuah fungsi yang nilai-nilainya diketahui secara diskrit (bukan rumus eksplisit).
- Menggunakan pendekatan Newton-Gregory Backward hingga Δ⁴.
- Menampilkan proses verbose atau langkah per langkah.

---

##  Struktur Fungsi

### 1. `build_backward_deltaerence_table(nilai_X, nilai_Y)`
Membangun tabel selisih mundur:
- Mengurutkan data dari kanan ke kiri (karena backward).
- Membentuk tabel bertingkat: Δy, Δ²y, Δ³y, ...

### 2. `extract_deltas_at_x0(x_st, table, x0)`
Mengambil elemen-elemen dari kolom yang sesuai dengan titik \( x_0 \), yaitu:
- Δy, Δ²y, Δ³y, Δ⁴y dari titik \( x_0 \).

### 3. `derivative_ng_backward_verbose(nilai_X, nilai_Y, x0, x)`
Melakukan perhitungan turunan dengan rumus:
\[
f'(x) = \frac{1}{h} \left[
  \Delta y +
  \frac{(2s+1)}{2} \Delta^2 y +
  \frac{(3s^2 + 6s + 2)}{6} \Delta^3 y +
  \frac{(4s^3 + 18s^2 + 22s + 6)}{24} \Delta^4 y
\right]
\]
- Di mana \( h \) adalah selisih antar \( x \), dan \( s = \frac{x - x_0}{h} \).
- Menampilkan semua langkah perhitungan secara rinci.

---

##  Contoh Penggunaan

```python
nilai_X = [2, 4, 6, 8, 10, 12, 14, 16, 18]
nilai_Y = [-940, -6008, -11652, 1040, 74020, 279960, 729932, 1581088, 3044340]

x0 = 10
x = 11

result = derivative_ng_backward_verbose(nilai_X, nilai_Y, x0, x)
print(f"\nHasil akhir turunan f'({x}) ≈ {result}")
```
R07
- Arya Raka F. (5053241007)
- Kelvin Aubert J. (5053241044)
- Syafiq Ahmad I. (5053241037)
- Arya Ramadhan (5053241033)
- M.Akbar Handoko B. (5053241023)
