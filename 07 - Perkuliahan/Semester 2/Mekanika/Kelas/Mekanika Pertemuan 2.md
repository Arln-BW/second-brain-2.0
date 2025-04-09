---
tags: 
Time: 2025-02-28T03:43:00
Links:
---
---
## Vektor dan Sistem Koordinat 3 Dimensi
### 1. Koordinat Kartesian
```tikz
\usetikzlibrary {3d}
\begin{document}
\begin{tikzpicture}[->, scale=1]
  \draw (0,0,0) -- (0,5,0) node[above] {$z$};
  \draw (0,0,0) -- (5,0,0) node[below] {$x$}; 
  \draw (0,0,0) -- (0,0,5) node[left] {$y$}; 
  \draw[color=red, thick] (0,0,0) -- (4,4,4) node[right] {$\overrightarrow{r}$};

  %\draw[dashed] (3,3,3) -- (0,3,3); % Tegak lurus ke sumbu x (ke bidang yz)
  \draw[dashed] (4,4,4) -- (4,0,4); % Tegak lurus ke sumbu y (ke bidang xz)
  \draw[dashed] (0,4,0) -- (4,4,4);
  \draw[dashed] (0,0,0) -- (4,0,4);
  %\draw[dashed] (3,3,3) -- (3,3,0); % Tegak lurus ke sumbu z (ke bidang xy)
  
  %\fill[black] (0,3,3) circle (1.5pt); % Titik proyeksi ke bidang yz
  \fill[black] (4,0,4) circle (1.5pt); % Titik proyeksi ke bidang xz
  %\fill[black] (3,3,0) circle (1.5pt); % Titik proyeksi ke bidang xy
\end{tikzpicture}
\end{document} 
```
### 2. Koordinat Silinder
```tikz
\usetikzlibrary {3d}
\begin{document}
\begin{tikzpicture}[->, scale=1]
  \draw (0,0,0) -- (0,5,0) node[above] {$z$};
  \draw (0,0,0) -- (5,0,0) node[below] {$x$}; 
  \draw (0,0,0) -- (0,0,5) node[left] {$y$}; 
  \draw[color=red, thick] (0,0,0) -- (4,0,4) node[right] {$\overrightarrow{r}$};

  %\draw[dashed] (3,3,3) -- (0,3,3); % Tegak lurus ke sumbu x (ke bidang yz)
  \draw[dashed] (4,4,4) -- (4,0,4); % Tegak lurus ke sumbu y (ke bidang xz)
  %\draw[dashed] (0,4,0) -- (4,4,4);
  \draw[dashed] (0,0,0) -- (4,4,4);
  
  %\fill[black] (0,3,3) circle (1.5pt); % Titik proyeksi ke bidang yz
  \fill[black] (4,0,4) circle (1.5pt); % Titik proyeksi ke bidang xz
  %\fill[black] (3,3,0) circle (1.5pt); % Titik proyeksi ke bidang xy
  \draw[blue] (0,0,1) arc (53.74:90:-1) node[midway, right] {$\theta$};
\end{tikzpicture}
\end{document}
```

### 3. Koordinat Bola

```tikz
\usetikzlibrary {3d}
\begin{document}
\begin{tikzpicture}[->, scale=1]
  \draw (0,0,0) -- (0,5,0) node[above] {$z$};
  \draw (0,0,0) -- (5,0,0) node[below] {$x$}; 
  \draw (0,0,0) -- (0,0,5) node[left] {$y$}; 
  \draw[color=red, thick] (0,0,0) -- (4,4,4) node[right] {$\overrightarrow{r}$};
  \draw[color=red, thick] (0,0,0) -- (0,4,4) node[right] {$\overrightarrow{r}$};

  %\draw[dashed] (3,3,3) -- (0,3,3); % Tegak lurus ke sumbu x (ke bidang yz)
  \draw[dashed] (4,4,4) -- (4,0,4); % Tegak lurus ke sumbu y (ke bidang xz)
  \draw[dashed] (0,4,0) -- (4,4,4);
  \draw[dashed] (0,0,0) -- (4,0,4);
  %\draw[dashed] (3,3,3) -- (3,3,0); % Tegak lurus ke sumbu z (ke bidang xy)
  
  %\fill[black] (0,3,3) circle (1.5pt); % Titik proyeksi ke bidang yz
  \fill[black] (4,0,4) circle (1.5pt); % Titik proyeksi ke bidang xz
  \draw[blue] (0,0.8,0) arc (90:54.74:1) node[midway, right] {$\theta$};
  %\fill[black] (3,3,0) circle (1.5pt); % Titik proyeksi ke bidang xy
\end{tikzpicture}
\end{document} 
```

```tikz
\usetikzlibrary {3d}
\begin{document}
\begin{tikzpicture}[z={(10:10mm)},x={(-45:5mm)}]
  \def\wave{
    \draw[fill,thick,fill opacity=.2]
     (0,0) sin (1,1) cos (2,0) sin (3,-1) cos (4,0)
           sin (5,1) cos (6,0) sin (7,-1) cos (8,0)
           sin (9,1) cos (10,0)sin (11,-1)cos (12,0);
    \foreach \shift in {0,4,8}
    {
      \begin{scope}[xshift=\shift cm,thin]
        \draw (.5,0)  -- (0.5,0 |- 45:1cm);
        \draw (1,0)   -- (1,1);
        \draw (1.5,0) -- (1.5,0 |- 45:1cm);
        \draw (2.5,0) -- (2.5,0 |- -45:1cm);
        \draw (3,0)   -- (3,-1);
        \draw (3.5,0) -- (3.5,0 |- -45:1cm);
      \end{scope}
    }
  }
  \begin{scope}[canvas is zy plane at x=0,fill=blue]
    \wave
    \node at (6,-1.5) [transform shape] {medan magnet};
  \end{scope}
  \begin{scope}[canvas is zx plane at y=0,fill=red]
    \draw[help lines] (0,-2) grid (12,2);
    \wave
    \node at (6,1.5) [rotate=180,xscale=-1,transform shape] {gelombang listrik};
  \end{scope}
\end{tikzpicture}
\end{document}
```


```tikz
\usepackage{pgfplots} 
\pgfplotsset{compat=1.16} 
\begin{document} 
\begin{tikzpicture} 
\begin{axis}[colormap/viridis] 
\addplot3[ surf, samples=18, domain=-3:3 ] {exp(-x^2-y^2)*x}; 
\end{axis} 
\end{tikzpicture} 
\end{document}
```

```tikz
\usepackage{tikz}
\usepackage{tikz-3dplot}
\usetikzlibrary{arrows.meta}

\begin{document}

\tdplotsetmaincoords{75}{110} % Sudut pandang untuk plot 3D

\begin{tikzpicture}[tdplot_main_coords, scale=1.5]

    % Menggambar sumbu koordinat
    \draw[thick, -Stealth] (0,0,0) -- (5,0,0) node[anchor=north east]{$x$};
    \draw[thick, -Stealth] (0,0,0) -- (0,3,0) node[anchor=north west]{$y$};
    \draw[thick, -Stealth] (0,0,0) -- (0,0,3) node[anchor=south]{$z$};

    % Menggambar bola
    \tdplotsetrotatedcoords{0}{0}{0}
    \draw[tdplot_rotated_coords, dashed] (0,0,0) circle (2); % Lingkaran pada bidang xy
    \tdplotsetrotatedcoords{90}{0}{0}
    \draw[tdplot_rotated_coords, dashed] (0,0,0) circle (2); % Lingkaran pada bidang xz
    \tdplotsetrotatedcoords{0}{90}{0}
    \draw[tdplot_rotated_coords, dashed] (0,0,0) circle (2); % Lingkaran pada bidang yz

    % Menentukan koordinat titik P dalam koordinat bola (r, theta, phi)
    \tdplotsetcoord{P}{2}{45}{45} % r=2, theta=45, phi=45

    % Menggambar titik P dan labelnya
    \fill (P) circle (2pt) node[anchor=south west]{$P(r,\theta,\phi)$};

    % Menggambar garis dari pusat ke titik P
    \draw[dashed] (0,0,0) -- (P);

    % Menggambar proyeksi titik P pada bidang xy
    \draw[dashed] (P) -- (Pxy);
    \draw[dashed] (0,0,0) -- (Pxy);

    % Menggambar sudut theta (antara sumbu z dan garis OP)
    \tdplotdrawarc{(0,0,0)}{0.5}{0}{45}{anchor=south west}{$\theta$}

    % Menggambar sudut phi (pada bidang xy, antara sumbu x dan proyeksi OP)
    \tdplotsetthetaplanecoords{45}
    \tdplotdrawarc[tdplot_rotated_coords]{(0,0,0)}{0.5}{0}{45}{anchor=south east}{$\phi$}

\end{tikzpicture}

\end{document}
```
