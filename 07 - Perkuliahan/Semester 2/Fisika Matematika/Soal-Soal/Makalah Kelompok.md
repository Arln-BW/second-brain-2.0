---
tags: 
Time: 
Links:
---
---
## 1. Topik Listrik AC Inverter
```python
import numpy as np
import matplotlib.pyplot as plt

# Parameter
Vm = 220  # Amplitudo (V)
f = 50    # Frekuensi (Hz)
omega = 2 * np.pi * f  # Frekuensi sudut (rad/s)
T = 1 / f  # Periode (s)

# Waktu
t = np.linspace(0, 2*T, 1000)

# Gelombang kotak (manual)
V = np.where(t % T < T/2, Vm, -Vm)

# Deret Fourier (5 harmonik pertama: n = 1, 3, 5, 7, 9)
n_terms = [1, 3, 5, 7, 9]
V_fourier = np.zeros_like(t)
for n in n_terms:
    V_fourier += (880 / (n * np.pi)) * np.sin(n * omega * t)

# Grafik
plt.figure(figsize=(12, 5))

# Sinyal vs Waktu
plt.subplot(1, 2, 1)
plt.plot(t, V, label='Gelombang Kotak (Asli)', color='blue')
plt.plot(t, V_fourier, '--', label='Aproksimasi Fourier (5 harmonik)', color='red')
plt.title('Sinyal AC Gelombang Kotak (220V, 50 Hz)')
plt.xlabel('Waktu (s)')
plt.ylabel('Tegangan (V)')
plt.grid(True)
plt.legend()

# Spektrum Frekuensi
frek = [n * f for n in n_terms]
amplitudo = [880 / (n * np.pi) for n in n_terms]
plt.subplot(1, 2, 2)
plt.stem(frek, amplitudo, basefmt=" ")
plt.title('Spektrum Frekuensi Harmonik')
plt.xlabel('Frekuensi (Hz)')
plt.ylabel('Amplitudo (V)')
plt.grid(True)

plt.tight_layout()
plt.show()
```


> [!NOTE] References
> 1. AI 1 : https://grok.com/share/bGVnYWN5_9364cd3e-e09c-441a-be05-8c8319f39bdc
> 2. AI 2 : https://grok.com/share/bGVnYWN5_d9889e6d-8fac-4ae2-8481-ae433740a08e
> 3. AI 3 (Deepseek) : https://chat.deepseek.com/a/chat/s/13e20c15-9f2a-4d30-9778-d2ff71c57645

---
1. oke, saat ini saya sedang menyusun suatu makalah tentang aplikasi deret fourier pada bidang atau konsep fisika dan saya ingin mengambil topik mekanika gelombang : analisis getaran dan gelombang suara. Oleh karena itu tolong berikan struktur yang tepat pada makalah yang ingin saya buat tentang topik tersebut
2. ternyata ingin mengganti topiknya, apakah bisa digunakan untuk konsep fisika dasar tentang listrik AC karena tema hanya sebatas "APLIKASI DERET FOURIER DALAM FISIKA DAN SAINS" dan hanya diperboleh kan menggunakan deret fourier yang digunakan pada sinya periodik atau mengulang setiap interval tertentu, jadi tolong perbaiki
3. bisa berikan contoh perhitungannya untuk sinyal AC pada tegangan AC rumah tangga (220V, 50 Hz) dan Analisis sinyal AC sinusoidal murni. Sertakan juga bagaimana bentuk grafiknya dalam python
4. karena sinyal ac sinusoidal murni seperti teganan rumah tangga tidak memiliki harmonik, maka dari itu berikan perjelasan serta perhitungan untuk sinyal AC dari peralatan elektronik (inverter, rectifier) yang menghasilkan gelombang kotak atau segitiga


Aplikasi Deret Fourier Dalam Fisika Dan Sains : Konsep Kerja Inverter dalam Mengubah Arus DC ke AC


## Abstrak
## Bab 1: Pendahuluan
## Bab 2: Dasar Teori
## Bab 3: Metode Analisis
## Bab 4: Hasil dan Pembahasan
## Bab 5: Kesimpulan dan Saran
## Daftar Pustaka
## Lampiran (Opsional)




















