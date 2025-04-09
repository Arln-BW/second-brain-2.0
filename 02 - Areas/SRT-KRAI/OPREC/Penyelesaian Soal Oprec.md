---
tags: 
Links: "[[My Areas]]"
---
---
## 1. Pendeteksi Rintangan
input :
- Baris pertama berisi koordinat titik awal dan akhir $(x_1, y_1)$ dan $(x_2, y_2)$
- Baris kedua berisi N banyaknya halangan
- Baris ketiga sampai N+2 berisi angka $(c_x, c_y, r)$ yang merupakan representasi halangan
Output :
- Banyaknya halangan yang akan bersinggungan dengan garis lintasan robot
Batasan: 
- Semua input bilangan (x1, y1, x2, y2, N, cx, cy, r) bertipe integer atau bilangan bulat. 
- Output berupa integer atau bilangan bulat.
Contoh Input : 
```pseudocode
1 1 3 1
3
2 1 1
4 1 1
3 3 1
```
Contoh Output :
```pseudocode
2
```

Pengerjaan :
1. Cari persamaan garis dengan subtitusi $m$ dari persamaan dua garis
$$m=\frac{y_2-y_1}{x_2-x_1} \hspace{3mm} dan \hspace{3mm} y-y_1=m(x-x_1)$$
2. Didapatkan persamaan sebagai berikut :
$$(y_2-y_1)x+(-(x_2-x_1))y+(x_2.y_1-y_2.x_1)=0$$
3. Bisa dimisalkan :
	- $A = y_2 - y_1$
	- $B = -(x_2-x_1)$
	- $C = x_2.y_1-y_2.y_1$
4. Rumus untuk menghitung jarak dari titik ke garis $Ax+By+C=0$ adalah
$$Jarak = \frac{\mid Ax+By+C \mid}{\sqrt{A^2 + B^2}}$$
5. Cek nilai jarak dengan jari- jari halangan apakah nilai dari $jarak \leq r$. Jika bernilai benar maka robot bersinggungan dengan halangan, jika tidak maka robot tidak bersinggungan dengan halangan.
6. Untuk menentukan seberapa banyak halangan yang bersinggungan, maka input nilai dari $(c_x, c_y, r)$ akan diulang sebanyak halangan yang ada.

## 2. Mekanik sdank sybuck
```python
# elements = [float(input()) for i in range(9)]
elements = [
    49961578496.000000, 22845.121094, -311177760.000000,
    22845.121094, 11434104672.000000, 97659.367188,
    -311177760.000000, 97659.367188, 64419688448.000000
] 

size = 3
matriks = [[0, 0, 0],
           [0, 0, 0],
           [0, 0, 0]]

# Mengisi matriks berdasarkan logika tertentu
for i in range(size):
    for j in range(size):
        if j > i:
            matriks[i][j] = elements.pop(0)
        elif i > j:
            matriks[i][j] = "\t"
        else:
            matriks[i][j] = elements.pop(0)

# Output matriks hasil
print(f'<inertia ixx="{matriks[0][0]:.6e}" ixy="{matriks[0][1]:.6e}" ixz="{matriks[0][2]:.6e}" \n'
    f'\t\t\t    iyy="{matriks[1][1]:.6e}" iyz="{matriks[1][2]:.6e}" \n\t\t\t\t\t\tizz="{matriks[2][2]:.6e}" />')
```
## 3. Kinematika Robot Sederhana
Untuk topik ini diketahui :
- $L_1 = L_2 = L_3 = 21cm = 0.21m$
- $\alpha_1 = 90 \degree$
- $\alpha_2 = 210 \degree$
- $\alpha_3 = 330 \degree$
### No. 1a dan 1b gunakan forward kinematics untuk menentukan $v_1, v_2, v_3$
$$
\begin{bmatrix} v_1 \\[0.3em] v_2 \\[0.3em]v_3 \end{bmatrix} =
\begin{bmatrix}
    -sin(\alpha_1) & cos(\alpha_1) & L_1 \\[0.3em]
    -sin(\alpha_2) & cos(\alpha_2) & L_2  \\[0.3em]
    -sin(\alpha_3) & cos(\alpha_3) & L_3 
\end{bmatrix}
\begin{bmatrix}
	u \\[0.3em]
	v \\[0.3em]
	\omega \\[0.3em]
\end{bmatrix}
$$
#### 1. a). $u = 10, v = 8, \omega = 3$
$\to$ $v_1 = -10\hspace{1mm}sin(90°)+8\hspace{1mm}cos(90°)+3\hspace{1mm}(0.21) = -9.37 \hspace{1mm} m/s$
$\to$$v_2 = -10\hspace{1mm}sin(210°)+8\hspace{1mm}cos(210°)+3\hspace{1mm}(0.21) = -1.298 \hspace{1mm} m/s$
$\to$ $v_2 = -10\hspace{1mm}sin(330°)+8\hspace{1mm}cos(330°)+3\hspace{1mm}(0.21) = 12,558 \hspace{1mm} m/s$
#### 1. b). $u = 11, v = 16, \omega = 0$
$\to$$v_1 = -11\hspace{1mm}sin(90°)+16\hspace{1mm}cos(90°)+0\hspace{1mm}(0.21) = -11 \hspace{1mm} m/s$
$\to$$v_2 = -11\hspace{1mm}sin(210°)+16\hspace{1mm}cos(210°)+0\hspace{1mm}(0.21) = -8.356 \hspace{1mm} m/s$
$\to$$v_3 = -11\hspace{1mm}sin(330°)+16\hspace{1mm}cos(330°)+0\hspace{1mm}(0.21) = 19.356 \hspace{1mm} m/s$
### No. 2a dan 2b gunakan invers kinematics untuk menentukan $u, v, \omega$
$$
\begin{bmatrix} u \\[0.3em] v \\[0.3em]\omega \end{bmatrix} =
\begin{bmatrix}
    -sin(\alpha_1)&-sin(\alpha_2)&-sin(\alpha_3) \\[0.3em]
    cos(\alpha_1) & cos(\alpha_2) & cos(\alpha_3) \\[0.3em]
    L_1 & L_2 & L_3
\end{bmatrix}
\begin{bmatrix}
	v_1 \\[0.3em]
	v_2 \\[0.3em]
	v_3 \\[0.3em]
\end{bmatrix}
$$
#### 2. a). $v_1 = 26, v_2 = 17, v_3 = 10$
$\to$$u = -26\hspace{1mm}sin(90°)-(17)\hspace{1mm}sin(210°)-10\hspace{1mm}sin(330°) = -12.5 \hspace{1mm} m/s$
$\to$$v = 26\hspace{1mm}cos(90°)+(17)\hspace{1mm}sin(210°)+10\hspace{1mm}sin(330°) = -8,34 \hspace{1mm} m/s$
$\to$$\omega = 26\hspace{1mm}(0.21) + (17)\hspace{1mm}(0.21) + 10\hspace{1mm}(0.21) = 11.13 \hspace{1mm} m/s$
#### 2. b). $v_1 = 9, v_2 = -23, v_3 = 14$
$\to$$u = -9\hspace{1mm}sin(90°)-(23)\hspace{1mm}sin(210°)-14\hspace{1mm}sin(330°) = -13.5 \hspace{1mm} m/s$
$\to$$v = 9\hspace{1mm}cos(90°)+(-23)\hspace{1mm}sin(210°)+14\hspace{1mm}sin(330°) = 32.042 \hspace{1mm} m/s$
$\to$$\omega = 9\hspace{1mm}(0.21) + (-23)\hspace{1mm}(0.21) + 14\hspace{1mm}(0.21) = 0 \hspace{1mm} m/s$
### No. 3 Gunakan invers kinematics terlebih dahulu untuk menentukan kecepatan disumbu-x dan sumbu-y dan memasukkan parameter jari-jari roda
Diketahui :
- $v_1 = 5, v_2 = 20, v_3 = -28$
- $t = 30\hspace{1mm}s$
- $r = 3 \hspace{1mm} = 0.03 \hspace{1mm} m$
- $L_1 = L_2 = L_3 = 0.21 m$
Cari kecepatan disumbu-x dan sumbu-y dengan menggunakan rumus kinematika maju
$$
\begin{bmatrix} u \\[0.3em] v \\[0.3em]\omega \end{bmatrix} = 
\frac{r}{3}
\begin{bmatrix}
    -sin(90\degree)&-sin(210\degree)&-sin(330\degree) \\[0.3em]
    cos(90\degree) & cos(210\degree) & cos(330\degree) \\[0.3em]
    L_1 & L_2 & L_3
\end{bmatrix}
\begin{bmatrix}
	v_1 \\[0.3em]
	v_2 \\[0.3em]
	v_3 \\[0.3em]
\end{bmatrix}
$$
Hitung nilai trigonometrinya dan subtitusikan nilai dari $r, L_1, L_2, L_3, v_1, v_2, v_3$ ehingga didapatkan
$$
\begin{bmatrix} u \\[0.3em] v \\[0.3em]\omega \end{bmatrix} = 
0.01
\begin{bmatrix}
    -9 \\[0.3em]
    -41.568  \\[0.3em]
    -0.63 
\end{bmatrix} = 
\begin{bmatrix}
	-0.09 \\[0.3em]
	-0.41568 \\[0.3em]
	-0.0068 \\[0.3em]
\end{bmatrix}
$$
Cari besar resultan kecepatan dengan rumus
$$\mid \overrightarrow{v} \mid = \sqrt{u^2 + v^2}$$
$$ \mid \overrightarrow{v} \mid = \sqrt{(-0.09)^2 + (-0,41568)^2} = 0.4252 \hspace{1.5mm} m/s$$
Cari jarak tempuh robot dengan rumus : 
$$\Delta x = \hspace{1mm}\mid \overrightarrow{v}\mid \times \hspace{1mm} t$$
$$\Delta x = \hspace{1mm}0.4252\hspace{1mm}m/s \times \hspace{1mm} 30 \hspace{1mm} s = 12.752 \hspace{1.5mm}meter$$
