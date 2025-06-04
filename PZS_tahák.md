# PZS/DSP Tahák

## Základní diskrétní signály

### Jednotkový impulz (Dirac delta)

$$
\delta[n] =
\begin{cases}
1 & n = 0 \\
0 & n \neq 0
\end{cases}
$$

### Jednotkový skok (unit step)

$$
u[n] =
\begin{cases}
1 & n \geq 0 \\
0 & n < 0
\end{cases}
$$

## Komplexní exponenciála a Eulerova formule

$$
e^{j\omega_0 n} = \cos(\omega_0 n) + j \sin(\omega_0 n)
$$

## Konvoluce v časové oblasti

Výpočet:
$$
y[n] = x[n] * h[n] = \sum_{k=-\infty}^{\infty} x[k] \cdot h[n - k]
$$

- Délka výsledku: $L_y = L_x + L_h - 1$
- Index počátku: $n_{\text{start}} = n_{x,\text{start}} + n_{h,\text{start}}$
- Index konce: $n_{\text{end}} = n_{x,\text{end}} + n_{h,\text{end}}$

## Konvoluce ve frekvenční oblasti

$$
Y(e^{j\omega}) = X(e^{j\omega}) \cdot H(e^{j\omega})
$$

## Kruhová konvoluce

$$
y[n] = \sum_{k=0}^{N-1} x[k] \cdot h[(n - k) \mod N]
$$

## Vlastnosti LTI systémů

| Vlastnost     | Podmínka                                        |
|---------------|--------------------------------------------------|
| Linearita     | Superpozice: homogenita + aditivita             |
| Kauzalita     | $h[n] = 0$ pro $n < 0$                           |
| Stabilita     | $\sum_n \|h[n]\| < \infty$                         |
| Časová invariance | $x[n-n_0] \Rightarrow y[n-n_0]$              |


## DTFT – Vybrané páry

| Sekvence | DTFT |
|---|---|
| $\delta[n]$ | $1$ |
| $\delta[n - n_0]$ | $e^{-j\omega n_0}$ |
| $1$ | $2\pi \delta(\omega)$ |
| $e^{jn\omega_0}$ | $2\pi\delta(\omega - \omega_0)$ |
| $\alpha^n u[n], \alpha < 1$ | $\frac{1}{1 - \alpha e^{-j\omega}}$ |
| $-\alpha^n u[-n - 1], \alpha > 1$ | $\frac{1}{1 - \alpha e^{j\omega}}$ |
| $(n+1)\alpha^n u[n]$, $\alpha < 1$ | $\frac{1}{(1 - \alpha e^{-j\omega})^2}$|
| $\cos(n\omega_0)$ | $\pi[\delta(\omega - \omega_0) + \delta(\omega + \omega_0)]$ |

### DTFT

$$
X[e^{j\omega}] = \sum_{n=-\infty}^{\infty} x[n] e^{-j \omega n}
$$

### Inverzní DTFT

$$
x[n] = \frac{1}{2\pi} \int_{-\pi}^{\pi} X[e^{j\omega}] e^{j \omega n} d\omega
$$

### Frekvenční vzorky

$$
\omega_k = \frac{2\pi k}{N}
$$

## Z-transformace – Vybrané páry

| Sekvence | $X(z)$ | ROC |
|---|---|---|
| $\delta[n]$ | $1$ | celá z-rovin |
| $\alpha^n u[n]$ | $\frac{1}{1 - \alpha z^{-1}}$ | $\|z\| > \alpha$ |
| $-\alpha^n u[-n - 1]$ | $\frac{1}{1 - \alpha z^{-1}}$ | $\|z\| < \alpha$ |
| $n\alpha^n u[n]$ | $\frac{\alpha z^{-1}}{(1 - \alpha z^{-1})^2}$ | $\|z\| > \alpha$ |
| $-n\alpha^n u[-n - 1]$ | $\frac{\alpha z^{-1}}{(1 - \alpha z^{-1})^2}$ | $\|z\| < \alpha$ |
| $\cos(\omega_0 n)u[n]$ | $\frac{1 - (\cos(\omega_0)z^{-1})}{1 - (2\cos(\omega_0)z^{-1}) + z^{-2}}$ | $\|z\| > 1$ |
| $\sin(\omega_0 n)u[n]$ | $\frac{\sin(\omega_0)z^{-1}}{1 - 2(\cos(\omega_0)z^{-1}) + z^{-2}}$ | $\|z\| > 1$ |

## Přenosová funkce (Transfer function)

Obecně:
$$
H(z) = \frac{Y(z)}{X(z)} = \frac{\sum b_k z^{-k}}{1 + \sum a_k z^{-k}}
$$

Rozdílová rovnice:
$$
y[n] = \sum b_k x[n - k] - \sum a_k y[n - k]
$$

## Energie a výkon signálu

- **Energie signálu**:

$$
E_x = \sum_{n=-\infty}^{\infty} x[n]^2
$$

- **Výkon signálu**:

$$
P_x = \frac{1}{N} \sum_{n=0}^{N-1} x[n]^2
$$

## Decibel a SNR

- **Změna energie (dB)**:

$$
dB = 10 \log_{10} \left( \frac{E_2}{E_1} \right)
$$

- **Změna amplitudy (dB)**:

$$
dB = 20 \log_{10} \left( \frac{A_2}{A_1} \right)
$$

- **SNR**:

$$
SNR = 10 \log_{10} \left( \frac{P_{\text{signal}}}{P_{\text{noise}}} \right)
$$

## Cross-correlation a Autocorrelation

- **Křížová korelace**:

$$
r_{xy}[l] = \sum_{k=-\infty}^{\infty} x[n + l] y[n]
$$

## DOA / TDOA

- **TDOA**:

$$
TDOA = l_{max} \cdot T_s
$$

$T_s$ je vzorkovací perioda, $l_{max}$ je maximální počet rozdílů mezi vzorky.

- **DOA**:

$$
DOA = \arcsin\left( \frac{c \cdot  TDOA}{d} \right)
$$

## Okna pro spektrální analýzu

- **Hammingovo okno**:

$$
w[n] = 0.54 - 0.46 \cos\left( \frac{2\pi n}{N - 1} \right)
$$

## Užitečné vztahy

- Délka konvoluce: $L_y = L_x + L_h - 1$
- DTFT $\cos(\omega_0 n)$: $\pi[\delta(\omega - \omega_0) + \delta(\omega + \omega_0)]$
- Z-transformace $\alpha^n u[n]$: $\frac{1}{1 - \alpha z^{-1}}$
- Vztah mezi analogovou a digitální frekvencí: $\omega = \frac{2\pi f}{f_s}$
