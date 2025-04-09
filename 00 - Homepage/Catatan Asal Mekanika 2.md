___
Diketahui :
- Kecepatan awal:  $\vec{V_0} = 10\hat{i} + 20\hat{j}$ (dalam m/s).
- Posisi awal: $(0, 0, 0)$.
## 1. Percepatan
$$\vec{a} = 0\hat{i} - 9.8\hat{j} \implies \vec{a}(t) = 0\hat{i} - 9.8\hat{j} \hspace{1mm} (m/s^2) $$
## 2. Kecepatan

- Kecepatan adalah integral dari percepatan terhadap waktu :
$$\vec{v}(t) = \vec{v}_0 + \int \vec{a} \text{ dt}$$
- Komponen kecepatan di sumbu-x dan sumbu-y :
$$v_x(t) = v_{0x} + \int 0 \text{ dt} = 10 \text{ (konstan)} \text{ dan } v_y(t) = v_{0y} + \int (-9.8) \text{ dt} = 20-9.8t$$
Jadi, kecepatan sebagai fungsi waktu:
$$\vec{v}(t) = 10 \vec i + (20-9.8t) \vec j \text{ m/s}$$
## 3. Posisi
- Posisi adalah integral dari kecepatan terhadap waktu:
$$\vec{r}(t) = \vec{r_0} + \int \vec{v}(t) \text{ dt}, \hspace{2mm} \text{ sehingga : } x(t) = \int v_x(t) \text{ dt} = 10 \text{ t} \hspace{2mm} \text{ dan } \hspace{2mm} y(t) = \int v_y(t) \text{ dt} = 20t-4.9t^2$$
Jadi, posisi sebagai fungsi waktu :
$$\vec{r}(t) = 10t \hat{i} + (20t-4.9t^2) \hat{j} \text{ (m)}$$
## 4. Transformasi ke Koordinat Silinder

- komponen jarak radial $\rho(t)$ dan sudut $\phi (t)$:
$$\rho(t) = \sqrt{x^2 + y^2} = \sqrt{(10t)^2 + (20t-4.9t^2)^2} = \sqrt{24.01t^4 - 196t^3 + 500 t^2}$$
$$\phi(t) = tan^{-1}\bigg(\frac{y(t)}{x(t)}\bigg) = tan^{-1}\bigg(\frac{20-4.9t}{10} \bigg)$$
- Lakukan penurunan $\rho(t)$ dan $\phi (t)$ terhadap waktu, didapatkan kecepatan $v_{\theta}$ dan $v_r$ :
$$v_\rho = \frac{d \rho(t)}{dt} = \frac{96.04t^3-588t^2+1000t}{2\sqrt{24.01t^4-196t^3+500t^2}} \hspace{3mm} dan \hspace{3mm} v_{\phi} = \rho.\frac{d\phi(t)}{dt} = \frac{-0.49}{1+(2-0.49)^2}$$


$$\rho = \sqrt{x^2+y^2}, \hspace{3mm} \phi = tan^{-1}\Big(\frac{y}{x}\Big), \hspace{3mm} z = z$$
