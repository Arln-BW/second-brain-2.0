---
tags: 
Time: 
Links:
---
---
## A. Deret Fourier dan Fungsi Ganjil-Genap
### 1. Deret Fourier
- Deret fourier menyatakan fungsi periodik
- Sebuah fungsi $f(x)$ dikatakan periodik dengan periode $T$, jika untuk setiap $x$ berlaku : $f(x+T) = f(x)$.

```tikz
\usepackage{tikz}

\begin{document}

\begin{tikzpicture}
    % Definisikan parameter
    \def\c{2} % Amplitudo c
    \def\piVal{3.14159} % Nilai pi untuk perhitungan
    \def\twoPiVal{2*\piVal} % 2pi
    \def\threePiVal{3*\piVal} % 3pi
    \def\fourPiVal{4*\piVal} % 4pi

    % Gambar sumbu x dan y
    \draw[->] (-\piVal-2.5,0) -- (\fourPiVal+2.5,0) node[right] {$x$}; % Sumbu x
    \draw[->] (0,-2.5) -- (0,2.5) node[above] {$f(x)$}; % Sumbu y

    % Tanda pada sumbu x
    \draw (-\piVal,0.1) -- (-\piVal,-0.1) node[below] {$-\pi$};
    \draw (0,0.1) -- (0,-0.1) node[below] {$0$};
    \draw (\piVal,0.1) -- (\piVal,-0.1) node[below] {$\pi$};
    \draw (\twoPiVal,0.1) -- (\twoPiVal,-0.1) node[below] {$2\pi$};
    \draw (\threePiVal,0.1) -- (\threePiVal,-0.1) node[below] {$3\pi$};
    \draw (\fourPiVal,0.1) -- (\fourPiVal,-0.1) node[below] {$4\pi$};

    % Tanda pada sumbu y
    \draw (-0.1,\c) -- (0.1,\c) node[right] {$c$};
    \draw (-0.1,-\c) -- (0.1,-\c) node[right] {$-c$};

    % Gambar gelombang persegi dengan warna merah untuk 2.5 periode
    \draw[thick, red] 
        (-\piVal,-\c) -- (-\piVal,0) -- (0,0) -- (0,\c) -- (\piVal,\c) -- (\piVal,0) -- % Periode 1: -pi ke pi
        (\piVal,-\c) -- (\twoPiVal,-\c) -- (\twoPiVal,0) -- (\threePiVal,0) -- % Periode 2: pi ke 3pi
        (\threePiVal,\c) -- (\fourPiVal,\c) -- (\fourPiVal,0); % Setengah periode: 3pi ke 4pi

    % Garis putus-putus untuk menunjukkan nilai c dan -c
    \draw[dashed] (-\piVal,\c) -- (\fourPiVal,\c);
    \draw[dashed] (-\piVal,-\c) -- (\fourPiVal,-\c);
\end{tikzpicture}

\end{document}
```

```tikz
\usepackage{tikz}

\begin{document}

\begin{tikzpicture}
    % Definisikan parameter
    \def\piVal{3.14159} % Nilai pi untuk perhitungan
    \def\twoPiVal{2*\piVal} % 2pi
    \def\threePiVal{3*\piVal} % 3pi
    \def\fourPiVal{4*\piVal} % 4pi

    % Gambar sumbu x dan y
    \draw[->] (-\piVal-0.5,0) -- (\fourPiVal+0.5,0) node[right] {$x$}; % Sumbu x
    \draw[->] (0,-1.5) -- (0,3.5) node[above] {$f(x)$}; % Sumbu y

    % Tanda pada sumbu x
    \draw (-\piVal,0.1) -- (-\piVal,-0.1) node[below] {$-\pi$};
    \draw (0,0.1) -- (0,-0.1) node[below] {$0$};
    \draw (\piVal,0.1) -- (\piVal,-0.1) node[below] {$\pi$};
    \draw (\twoPiVal,0.1) -- (\twoPiVal,-0.1) node[below] {$2\pi$};
    \draw (\threePiVal,0.1) -- (\threePiVal,-0.1) node[below] {$3\pi$};
    \draw (\fourPiVal,0.1) -- (\fourPiVal,-0.1) node[below] {$4\pi$};

    % Tanda pada sumbu y
    \draw (-0.1,1) -- (0.1,1) node[right] {$1$};
    \draw (-0.1,-1) -- (0.1,-1) node[right] {$-1$};

    % Gambar grafik sin(x) dengan warna merah
    \draw[thick, red, domain=-\piVal:\fourPiVal, samples=200] plot (\x, {sin(\x r)});

    % Garis putus-putus untuk menunjukkan nilai 1 dan -1
    \draw[dashed] (-\piVal,1) -- (\fourPiVal,1);
    \draw[dashed] (-\piVal,-1) -- (\fourPiVal,-1);
\end{tikzpicture}

\end{document}
```
```tikz
\usepackage{tikz}

\begin{document}

\begin{tikzpicture}
    % Definisikan parameter
    \def\piVal{3.14159} % Nilai pi untuk perhitungan
    \def\twoPiVal{2*\piVal} % 2pi
    \def\threePiVal{3*\piVal} % 3pi
    \def\fourPiVal{4*\piVal} % 4pi

    % Gambar sumbu x dan y
    \draw[->] (-\piVal-0.5,0) -- (\fourPiVal+0.5,0) node[right] {$x$}; % Sumbu x
    \draw[->] (0,-1.5) -- (0,1.5) node[above] {$f(x)$}; % Sumbu y

    % Tanda pada sumbu x
    \draw (-\piVal,0.1) -- (-\piVal,-0.1) node[below] {$-\pi$};
    \draw (0,0.1) -- (0,-0.1) node[below] {$0$};
    \draw (\piVal,0.1) -- (\piVal,-0.1) node[below] {$\pi$};
    \draw (\twoPiVal,0.1) -- (\twoPiVal,-0.1) node[below] {$2\pi$};
    \draw (\threePiVal,0.1) -- (\threePiVal,-0.1) node[below] {$3\pi$};
    \draw (\fourPiVal,0.1) -- (\fourPiVal,-0.1) node[below] {$4\pi$};

    % Tanda pada sumbu y
    \draw (-0.1,1) -- (0.1,1) node[right] {$1$};
    \draw (-0.1,-1) -- (0.1,-1) node[right] {$-1$};

    % Gambar grafik cos(x) dengan warna merah
    \draw[thick, red, domain=-\piVal:\fourPiVal, samples=200] plot (\x, {cos(\x r)});

    % Garis putus-putus untuk menunjukkan nilai 1 dan -1
    \draw[dashed] (-\piVal,1) -- (\fourPiVal,1);
    \draw[dashed] (-\piVal,-1) -- (\fourPiVal,-1);
\end{tikzpicture}

\end{document}
```
> [!NOTE] NOTE
> $$T = 2L, \text{ di mana dalam contoh ini } T = 2L = 2\pi, \text{ maka } L = \pi$$

