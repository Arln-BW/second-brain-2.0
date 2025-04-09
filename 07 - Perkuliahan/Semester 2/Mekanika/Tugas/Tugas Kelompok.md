---
tags: 
Time: 
Links:
---
---
## Koordinat Kartesius Gerak Parabola
```python
import numpy as np
import matplotlib.pyplot as plt

# Parameter
g = 9.8  # gravitasi (m/s^2)
v0y = 20  # kecepatan awal y (m/s)
t_total = 400  # waktu total (detik)

# Waktu pendaratan
t_land = 2 * v0y / g  # ~4.08 detik
v_land = v0y - g * t_land  # kecepatan saat mendarat (~-20 m/s)

# Rentang waktu
t = np.linspace(0, t_total, 1000)
y = np.zeros_like(t)  # array ketinggian

# Fase sebelum mendarat (di udara)
mask_air = t <= t_land
y[mask_air] = v0y * t[mask_air] - 0.5 * g * t[mask_air]**2

# Fase setelah mendarat (di dalam tanah)
mask_ground = t > t_land
t_ground = t[mask_ground] - t_land  # waktu relatif setelah mendarat
y[mask_ground] = v_land * t_ground - 0.5 * g * t_ground**2

# Plot waktu vs ketinggian
plt.figure(figsize=(12, 6))
plt.plot(t, y, label='Lintasan Vertikal')
plt.axhline(y=0, color='k', linestyle='--', label='Permukaan Tanah')
plt.xlabel('Waktu (s)')
plt.ylabel('Ketinggian (m)')
plt.title('Ketinggian terhadap Waktu (Benda Melesak ke Tanah, 0-400 detik)')
plt.grid(True)
plt.legend()

# Zoom inset untuk melihat parabola awal
from mpl_toolkits.axes_grid1.inset_locator import inset_axes
ax = plt.gca()
axins = inset_axes(ax, width="30%", height="30%", loc='upper right')
axins.plot(t, y)
axins.set_xlim(0, 5)
axins.set_ylim(-10, 25)
axins.axhline(y=0, color='k', linestyle='--')
axins.grid(True)

plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameter
g = 9.8  # gravitasi (m/s^2)
v0y = 20  # kecepatan awal y (m/s)
t_total = 400  # waktu total (detik)

# Waktu pendaratan
t_land = 2 * v0y / g  # ~4.08 detik
v_land = v0y - g * t_land  # kecepatan saat mendarat (~-20 m/s)

# Rentang waktu
t = np.linspace(0, t_total, 1000)
y = np.zeros_like(t)

# Fase sebelum mendarat (di udara)
mask_air = t <= t_land
y[mask_air] = v0y * t[mask_air] - 0.5 * g * t[mask_air]**2

# Fase setelah mendarat (di dalam tanah)
mask_ground = t > t_land
t_ground = t[mask_ground] - t_land
y[mask_ground] = v_land * t_ground - 0.5 * g * t_ground**2

# Membuat dua subplot
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 10), gridspec_kw={'height_ratios': [2, 1]})

# Subplot 1: Fase di udara (diperbesar)
ax1.plot(t[mask_air], y[mask_air], label='Lintasan di Udara', color='blue')
ax1.axhline(y=0, color='k', linestyle='--', label='Permukaan Tanah')
ax1.set_xlim(0, t_land)
ax1.set_ylim(-5, 25)  # Diperbesar untuk detail
ax1.set_xlabel('Waktu (s)')
ax1.set_ylabel('Ketinggian (m)')
ax1.set_title('Fase di Atas Tanah (Diperbesar)')
ax1.grid(True)
ax1.legend()

# Subplot 2: Fase di tanah (diperkecil)
ax2.plot(t[mask_ground], y[mask_ground], label='Lintasan di Tanah', color='red')
ax2.axhline(y=0, color='k', linestyle='--', label='Permukaan Tanah')
ax2.set_xlim(t_land, t_total)
ax2.set_ylim(y[mask_ground].min(), 0)  # Menunjukkan kedalaman penuh
ax2.set_xlabel('Waktu (s)')
ax2.set_ylabel('Ketinggian (m)')
ax2.set_title('Fase di Bawah Tanah (Diperkecil)')
ax2.grid(True)
ax2.legend()

plt.tight_layout()
plt.show()
```

---
## Koordinat silinder gerak parabola
```python
import numpy as np
import matplotlib.pyplot as plt

# Parameter
g = 9.8  # gravitasi (m/s^2)
v0y = 20  # kecepatan awal y (m/s)
v0x = 10  # kecepatan awal x (m/s) dari contoh awal
t_total = 400  # waktu total (detik)

# Waktu pendaratan
t_land = 2 * v0y / g  # ~4.08 detik
v_land = v0y - g * t_land  # kecepatan saat mendarat (~-20 m/s)

# Rentang waktu
t = np.linspace(0, t_total, 1000)
x = v0x * t  # posisi horizontal
z = np.zeros_like(t)  # ketinggian (z dalam silinder)

# Fase sebelum mendarat (di udara)
mask_air = t <= t_land
z[mask_air] = v0y * t[mask_air] - 0.5 * g * t[mask_air]**2

# Fase setelah mendarat (di dalam tanah)
mask_ground = t > t_land
t_ground = t[mask_ground] - t_land
z[mask_ground] = v_land * t_ground - 0.5 * g * t_ground**2

# Transformasi ke koordinat silinder
r = np.sqrt(x**2 + z**2)  # jarak radial
theta = np.arctan2(z, x)  # sudut (dalam radian)

# Plot dalam koordinat silinder
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 8))

# Plot r vs t
ax1.plot(t, r, label='Jarak Radial (r)', color='blue')
ax1.set_xlabel('Waktu (s)')
ax1.set_ylabel('r (m)')
ax1.set_title('Jarak Radial terhadap Waktu')
ax1.grid(True)
ax1.legend()

# Plot theta vs t
ax2.plot(t, theta, label='Sudut (θ)', color='red')
ax2.set_xlabel('Waktu (s)')
ax2.set_ylabel('θ (radian)')
ax2.set_title('Sudut terhadap Waktu')
ax2.grid(True)
ax2.legend()

plt.tight_layout()

# Inset untuk memperjelas fase awal (0-5 detik)
from mpl_toolkits.axes_grid1.inset_locator import inset_axes
ax1_inset = inset_axes(ax1, width="30%", height="30%", loc='upper right')
ax1_inset.plot(t, r)
ax1_inset.set_xlim(0, 5)
ax1_inset.set_ylim(0, 25)
ax1_inset.grid(True)

ax2_inset = inset_axes(ax2, width="30%", height="30%", loc='upper right')
ax2_inset.plot(t, theta)
ax2_inset.set_xlim(0, 5)
ax2_inset.set_ylim(-0.5, 1.5)
ax2_inset.grid(True)

plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameter
g = 9.8  # gravitasi (m/s^2)
v0y = 20  # kecepatan awal y (m/s)
v0x = 10  # kecepatan awal x (m/s)
t_total = 400  # waktu total (detik)

# Waktu pendaratan
t_land = 2 * v0y / g  # ~4.08 detik
v_land = v0y - g * t_land  # kecepatan saat mendarat (~-20 m/s)

# Rentang waktu
t = np.linspace(0, t_total, 1000)
x = v0x * t  # posisi horizontal
z = np.zeros_like(t)  # ketinggian (z dalam silinder)

# Fase sebelum mendarat (di udara)
mask_air = t <= t_land
z[mask_air] = v0y * t[mask_air] - 0.5 * g * t[mask_air]**2

# Fase setelah mendarat (di dalam tanah)
mask_ground = t > t_land
t_ground = t[mask_ground] - t_land
z[mask_ground] = v_land * t_ground - 0.5 * g * t_ground**2

# Transformasi ke koordinat silinder
r = np.sqrt(x**2 + z**2)  # jarak radial
theta = np.arctan2(z, x)  # sudut (dalam radian)

# Plot theta vs r
plt.figure(figsize=(12, 6))
plt.plot(theta, r, label='r vs θ', color='purple')
plt.xlabel('θ (radian)')
plt.ylabel('r (m)')
plt.title('Jarak Radial (r) terhadap Sudut (θ)')
plt.grid(True)
plt.legend()

# Inset untuk memperjelas fase awal (di udara)
from mpl_toolkits.axes_grid1.inset_locator import inset_axes
ax = plt.gca()
axins = inset_axes(ax, width="30%", height="30%", loc='upper right')
axins.plot(theta, r)
axins.set_xlim(-0.5, 1.5)  # Fokus pada theta di fase awal
axins.set_ylim(0, 25)      # Fokus pada r kecil
axins.grid(True)

plt.show()
```

https://grok.com/share/bGVnYWN5_51a60ff6-3bfe-48b1-86bb-874c9af4ab65
