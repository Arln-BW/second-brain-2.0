---
tags: 
Area: "[[]]"
custom-width: .nan
---
---
1. Ilmu statistika deskriptif : simpangan rata-rata, variansi, standar deviasi
2. Ilmu statistika inferensial : distribusi binomial, variabel acak, hidden state(keadaan tersembunyi)
3. https://github.com/cra-ros-pkg/robot_localization/blob/ros2/params/ekf.yaml 
4. simpangan baku atau standar deviasi ($\sigma$) digunakan untuk mengetahui homogenitas data
5. variansi (${\sigma}^2$) digunakan untuk mengetahui sebaran data terhadap nilai rata-rata
6. variasi kalman filter : EKF (Extended Kalman Filter) dan UKF (Unscenterd Kalman Filter)

%% arlen240
@arlenbtn7 %%

---
## Distribusi Normal
7. distribusi normal adalah peluang distribusi yang berisi variabel acak x
8. grafik dari suatu normal distribusi biasa dikenal dengan kurva distribusi

Sebuah distribusi normal memiliki bebrapa properti di bawah ini:
9. mean, median dan modus
10. hasil dari kurva distribusi berbentuk lonceng yang titik tengahnya berada di titik mean atau simteris di titik mean
11. total dari luas di bawah kurva bernilai 1
12. kurva normal distribusi akan mendekati sumbu x tapi tidak akan pernah menyentuh sumbu x
13. diantara $\mu - \sigma$ dan $\mu + \sigma$ (antara tengah kurva), kurva grafik akan condong ke bawah. kurva yang condong ke atas berada di sisi kuri $\mu - \sigma$ dan $\mu + \sigma$
![[kurva-distribusi-normal.png#center|400]]
14. jika distribusi probabilitas diskrit dapat digambarkan dengan histogram
15. jika distribusi probabilitas kontinu dapat digunakan sebuah pdf(probability density function)
16. sebuah probability density function memiliki dua syarat : total area di bawah kurva sama dengan 1
17. fungsinya tidak pernah negatif
18. rumusnya : $$y = \frac{1}{\sigma \sqrt{2\pi}}e^{-(x-\mu)^2/(2\sigma^2)}$$
19. distribusi normal standar memiliki sebuah mean bernilai 0 dan standar debiasi bernilai 1
20. skala horizontal dari grafik distribusi normal standar berkoresponden ke z-scores $$z = \frac{value-mean}{standar deviasi} = \frac{x - \mu}{\sigma}$$
---
## Kalman Filter
21. merupakan proses berulang pada proses matematika yang mengikuti data input yang akan menjadi data output
22. perhitungan yang menjadi acuan akan menghasilkan nilai, posisi, kecepatan dan nilai lainnya
23. akan mendekati nilai yang merupakan nilai sebenarnya
24. nilai yang diperlukan merupakan target yang memiliki beberapa komponen :
$$\hat{x} = \begin{bmatrix} x \\[0.3em] y \\[0.3em] \dot{x} \\[0.3em] \dot{y} \end{bmatrix}$$
25. sistem dengan presisi tinggi memiliki pengukuran variansi yang rendah
26. ketika sistem dengan presisi rendah memiliki pengukuran variansi yang tinggi
27. sistem dengan presisi rendah dikenal dengan sistem bias (error)

---
## $\alpha$, $\beta$ dan $\gamma$ Filter
28. alpha filter ($\alpha$) : Digunakan untuk memperbaiki estimasi posisi. Semakin besar nilai $\alpha$, semakin cepat estimasi mengikuti pengukuran tetapi lebih sensitif terhadap noise
29. beta filter ($\beta$) : digunakan untuk memperbaiki estimasi kecepatan. Mengatur seberapa cepat estimasi kecepatan disesuaikan.
30. gamma filter ($\gamma$) : digunakan untuk memperbaiki estimasi percepatan. Membantu menangkap perubahan percepatan yang terjadi.
31. Prediksi (model gerak)
	1. $x_{pred} = x_{est} + v_{est} \Delta t + \frac{1}{2} a_{est}(\Delta t)^2$ 
	2. $v_{pred} = v_{est} + a_{est} \Delta t$
	3. $a_{pred} = a_{est}$
32. Koreksi (update dengan pengukuran baru)
	1. $x_{new} = x_{est} + \alpha(z - x_{pred})$
	2. $v_{new} = v_{est} + \beta \frac{z - x_{pred}}{\Delta t}$
	3. $a_{new} = a_{pred} + \gamma \frac{z - x_{pred}}{(\Delta t)^2}$ 
---
## Interpolasi & Ekstrapolasi
beberapa metode interpolasi atau ektrapolasi yang sering digunakan dalam penentuan data yang tidak diketahui berdasarkan ketelitian dan akurasi data :
1. formulasi newton maju
2. formulasi newton mundur
3. formulasi lagrange
Untuk formulasi newton maju maupun mundur dilakukan jika interval data tetap (sama) sedangkan formulasi lagrange digunakan karena terjadi perubahan interval data
### 1. Metode Newton Maju
$$f(x+n.h) = f(x) + n\Delta f(x) + \frac{n(n-1)}{2!} \Delta^2f(x)+...$$
### 2. Metode Newton Mundur
$$yn=y_0+n\Delta y_0 + \frac{n(n+1)}{2!}\Delta^2y_0+\frac{n(n+1)(n+2)}{3!}\Delta^3y_0+...$$
