---
tags: 
Links: "[[My Areas]]"
---
---
berikan skema perhitungan inverse kinematic dan forward kinematic pada penerapan 4 buah roda omni yang digunakan dalam menjalankan sebuah robot

###### ChatGPT said:

ChatGPT

Pada robot dengan **4 roda omni**, skema perhitungan **forward kinematics** dan **inverse kinematics** didasarkan pada model kinematika yang memperhitungkan arah dan kecepatan masing-masing roda. Berikut adalah skema dasar dan rumus untuk masing-masing:

---

### **1. Forward Kinematics (FK)**

**Forward kinematics** bertujuan menghitung kecepatan linier dan angular dari robot berdasarkan kecepatan sudut masing-masing roda.

#### Skema:

1. Tentukan parameter roda omni:
    
    - **α**: Sudut orientasi roda terhadap sumbu utama robot.
    - **r**: Radius roda.
    - **l**: Jarak roda dari pusat robot.
2. Hitung kecepatan robot (VxV_xVx​, VyV_yVy​, ωz\omega_zωz​) dalam kerangka robot.
    

#### Persamaan:

Kecepatan robot diberikan oleh:

$$ [VxVyωz]=r4[−sin⁡(α1)−sin⁡(α2)−sin⁡(α3)−sin⁡(α4)cos⁡(α1)cos⁡(α2)cos⁡(α3)cos⁡(α4)1l1l1l1l][ω1ω2ω3ω4]\begin{bmatrix} V_x \\ V_y \\ \omega_z \end{bmatrix} = \frac{r}{4} \begin{bmatrix} -\sin(\alpha_1) & -\sin(\alpha_2) & -\sin(\alpha_3) & -\sin(\alpha_4) \\ \cos(\alpha_1) & \cos(\alpha_2) & \cos(\alpha_3) & \cos(\alpha_4) \\ \frac{1}{l} & \frac{1}{l} & \frac{1}{l} & \frac{1}{l} \end{bmatrix} \begin{bmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \\ \omega_4 \end{bmatrix}​Vx​Vy​ωz​​​=4r​​−sin(α1​)cos(α1​)l1​​−sin(α2​)cos(α2​)l1​​−sin(α3​)cos(α3​)l1​​−sin(α4​)cos(α4​)l1​​​​ω1​ω2​ω3​ω4​​​$$

Dimana:

- ω1,ω2,ω3,ω4\omega_1, \omega_2, \omega_3, \omega_4ω1​,ω2​,ω3​,ω4​: Kecepatan sudut masing-masing roda.
- αi\alpha_iαi​: Sudut roda terhadap sumbu utama robot.

Output:

- VxV_xVx​: Kecepatan linier sumbu X.
- VyV_yVy​: Kecepatan linier sumbu Y.
- ωz\omega_zωz​: Kecepatan angular rotasi robot.

---

### **2. Inverse Kinematics (IK)**

**Inverse kinematics** digunakan untuk menentukan kecepatan sudut roda (ω1,ω2,ω3,ω4\omega_1, \omega_2, \omega_3, \omega_4ω1​,ω2​,ω3​,ω4​) berdasarkan kecepatan robot (Vx,Vy,ωzV_x, V_y, \omega_zVx​,Vy​,ωz​).

#### Skema:

1. Gunakan parameter roda yang sama seperti di FK.
2. Hitung kecepatan sudut roda dari kecepatan translasi dan rotasi robot.

#### Persamaan:

[ω1ω2ω3ω4]=1r[−sin⁡(α1)cos⁡(α1)l−sin⁡(α2)cos⁡(α2)l−sin⁡(α3)cos⁡(α3)l−sin⁡(α4)cos⁡(α4)l][VxVyωz]\begin{bmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \\ \omega_4 \end{bmatrix} = \frac{1}{r} \begin{bmatrix} -\sin(\alpha_1) & \cos(\alpha_1) & l \\ -\sin(\alpha_2) & \cos(\alpha_2) & l \\ -\sin(\alpha_3) & \cos(\alpha_3) & l \\ -\sin(\alpha_4) & \cos(\alpha_4) & l \end{bmatrix} \begin{bmatrix} V_x \\ V_y \\ \omega_z \end{bmatrix}​ω1​ω2​ω3​ω4​​​=r1​​−sin(α1​)−sin(α2​)−sin(α3​)−sin(α4​)​cos(α1​)cos(α2​)cos(α3​)cos(α4​)​llll​​​Vx​Vy​ωz​​​

Dimana:

- Input: Vx,Vy,ωzV_x, V_y, \omega_zVx​,Vy​,ωz​.
- Output: ω1,ω2,ω3,ω4\omega_1, \omega_2, \omega_3, \omega_4ω1​,ω2​,ω3​,ω4​.

---

### **Penerapan dalam Robot Omni 4 Roda**

- **FK** digunakan ketika Anda ingin mengetahui arah gerak dan rotasi robot berdasarkan kecepatan roda.
- **IK** digunakan ketika Anda ingin menentukan kecepatan roda berdasarkan arah dan rotasi yang diinginkan.

#### Contoh Parameter:

1. Roda omni ditempatkan dengan sudut α1=45∘,α2=135∘,α3=225∘,α4=315∘\alpha_1 = 45^\circ, \alpha_2 = 135^\circ, \alpha_3 = 225^\circ, \alpha_4 = 315^\circα1​=45∘,α2​=135∘,α3​=225∘,α4​=315∘.
2. Nilai rrr, lll, dan kecepatan masukan robot dapat disesuaikan.

Dengan rumus ini, skema kinematika dapat dimasukkan ke program kontrol untuk menentukan gerak robot secara presisi. Apakah Anda memerlukan implementasi dalam bentuk kode?

4o

##### You said:

l pada perhitungan tersebut apa?

###### ChatGPT said:

ChatGPT

Pada perhitungan kinematika robot omni, lll adalah **jarak radial** antara pusat massa (atau pusat rotasi) robot dengan titik kontak roda omni.

### Penjelasan:

- Robot omni biasanya memiliki roda yang dipasang pada sudut tertentu di sekeliling kerangka robot.
- **Pusat rotasi** adalah titik tengah robot, yang merupakan pusat gerakan rotasi (ωz\omega_zωz​).
- lll merepresentasikan **jari-jari lingkaran imajiner** yang menghubungkan pusat rotasi robot dengan posisi roda omni.

### Pentingnya Nilai lll:

1. **Rotasi Robot (ωz\omega_zωz​)**:
    
    - Ketika robot berotasi, setiap roda akan menghasilkan komponen kecepatan yang bergantung pada jaraknya dari pusat rotasi.
    - Semakin besar lll, semakin besar kecepatan sudut roda diperlukan untuk mencapai kecepatan rotasi tertentu.
2. **Stabilitas Robot**:
    
    - Nilai lll memengaruhi stabilitas dan distribusi gaya robot. Pada robot dengan desain persegi, lll biasanya sama untuk semua roda.
3. **Kesimetrian Perhitungan**:
    
    - Semua roda dalam robot omni memiliki nilai lll yang sama, sehingga persamaan menjadi simetris.

### Contoh Nilai lll:

Jika robot berbentuk persegi dengan jarak antar roda 20 cm, maka nilai lll biasanya adalah:

l=Diagonal Persegi2=(20)2+(20)22=14.14 cm.l = \frac{\text{Diagonal Persegi}}{2} = \frac{\sqrt{(20)^2 + (20)^2}}{2} = 14.14 \, \text{cm}.l=2Diagonal Persegi​=2(20)2+(20)2​​=14.14cm.

---

Apakah Anda membutuhkan simulasi atau implementasi lebih detail, seperti dalam bentuk program atau diagram?