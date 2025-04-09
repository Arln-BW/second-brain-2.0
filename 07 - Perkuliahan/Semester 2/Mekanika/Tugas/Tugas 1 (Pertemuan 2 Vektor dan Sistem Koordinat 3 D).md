---
tags: 
Time: 2025-03-01T21:39:00
Links:
---
---
## 1. Jelaskan kelebihan dan kekurangan dalam penggunaan sistem koordinat kartesian, silinder, dan bola untuk menyelesaikan masalah mekanika. Berikan juga contoh kasusnya.
Kelebihan sistem koordinat
1. Kartesian : mudah digunakan, bisa digunakan secara langsung dan mudah menerapkan integral dalam ruang persegi
2. Silinder : cocok untuk gerakan yang memiliki simetri sepanjang sumbu tertentu seperti pipa atau roda dan memudahkan analisis rotasi atau gerakan melingkar
3. Bola : Sangat efisien untuk masalah dengan simetri radial penuh seperti gerak gravitasi, medan magnet atau gerakan planet serta mudah untuk menggambarkan lintasan melengkung dalam 3 dimensi
Kekurangan sistem koordinat
1. kartesian : sulit untuk mengelesaikan masalah simetri silinder atau bola dan tidak praktis untuk jarak radial atau melingkar
2. silinder : perhitungan percepatan atau gaya dalam arah radial bisa menjadi rumit dan Tidak efisien untuk masalah yang memiliki simetri radial penuh seperti gravitasi planet
3. bola : Tidak praktis untuk objek atau gerakan yang tidak memiliki simetri bola, seperti balok atau bidang datar. Turunan terhadap waktu menjadi lebih rumit dan melibatkan banyak suku karena basis vektor ($\hat{e}r, \hat{e}\theta, \hat{e}\phi$) berubah tergantuk posisi ($r, \theta, \phi$).

```tikz 
\begin{document} 
\begin{tikzpicture}[domain=0:4] 
\draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9); 
\draw[->] (-1.2,0) -- (4.2,0) node[right] {$x$}; 
\draw[->] (0,-1.2) -- (0,4.2) node[above] {$y$};
\draw[color=red] plot (\x,\x) node[right] {$\overrightarrow{r}$};
\end{tikzpicture} 
\end{document}
```
## Diketahui posisi dua buah titik dalam koordinat bola adalah A(2, $\frac{\pi}{4}$, $\frac{\pi}{6}$) dan B(3, $\frac{\pi}{3}$, $\frac{\pi}{2}$). Ubah kedua posisi tersebut ke dalam koordinat kartesian lalu hitung perkalian vektor posisi A dan B.
### titik A($2,45\degree, 30 \degree$)
Diketahui :
- r = 2
- $\theta = 45 \degree$ 
- $\phi = 30 \degree$

Rumus :
- $x = r \hspace{2mm} sin \phi \hspace{2mm} cos \theta$ 
- $y = r \hspace{2mm} sin \phi \hspace{2mm} sin \theta$
- $z = r \hspace{2mm} cos \phi$ 

### titik B($3,60\degree, 90\degree$)
- r = 3
- $\theta = 60 \degree$
- $\phi = 90 \degree$

