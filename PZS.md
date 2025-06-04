# Počítačové zpracování signálu aneb Digital Signal Processing

## Lekce 1

### Co je diskrétní deterministický signál (časová notace)?

Konečná sekvence hodnot, které jsou vzorkovány v diskrétních časových okamžicích. Časová notace je obvykle vyjádřena jako $x[n]$, kde $n$ je celočíselný index.

### Co je diskrétní systém?

Matematický model, který popisuje vztah mezi vstupním a výstupním diskrétním signálem. Může být reprezentován pomocí diferenčních rovnic, impulsní odezvy nebo přenosové funkce.
$$y[n] = x[n]$$

### Jaké jsou elementární signály a jak se značí (jednotkový impuls, jednotkový skok, komplexní exponenciála)?

Jednotkový impuls je signál, který má hodnotu 1 v čase $n=0$ a 0 jinde, značí se $\delta[n]$.

Jednotkový skok je signál, který má hodnotu 0 pro $n<0$ a 1 pro $n\geq0$, značí se $u[n]$.

Komplexní exponenciála je signál ve tvaru $e^{j\omega n}$, kde $\omega$ je úhlová frekvence.

### Jaké jsou základní manipulace se signály (posun, zrcadlení, převzorkování)?

Posun signálu $x[n]$ o $k$ vzorků je dán vztahem $x[n-k]$.

Zrcadlení signálu $x[n]$ je dáno vztahem $x[-n]$.

Převzorkování zahrnuje změnu vzorkovací frekvence, což může zahrnovat buď zvýšení (interpolace) nebo snížení (decilace) počtu vzorků.

### Jaké jsou vlastnosti diskrétních systémů (bez paměti, kauzální, stabilní, lineární, časově invariantní)?

Bez paměti: Výstup závisí pouze na aktuálním vstupu, ne na předchozích hodnotách.

Kauzální: Výstup v čase $n$ závisí pouze na vstupech v čase $n$ a dřívějších (ne na budoucích).

Stabilní: Vstup omezeného výkonu vede k omezenému výstupu.

Aditivní: Výstup je lineární kombinací vstupů.

Homogení: Nezávisí na pořadí vstupů $T(c*x[n]) = c*T(x[n])$

Lineární: Systém splňuje princip superpozice, tj. $y[n] = a_1 x_1[n] + a_2 x_2[n]$.

### Co je LTI systém a jaké má modely v časové oblasti (diferenční rovnice, impulsní odezva)?

Linear time-invariant (LTI) systém je systém, který je lineární, aditivní, homogení a časově invariantní. V časové oblasti může být modelován pomocí diferenční rovnice nebo impulsní odezvy.

Impulsní odezva (IR) je reakce systému na jednotkový puls, značí se $h[n]$ a popisuje, jak systém reaguje na různé frekvence.

### Co je konvoluce diskrétních signálů, jaký má význam a vlastnosti?

Konvoluce diskrétních signálů je matematická operace, která kombinuje dva signály a vytváří nový signál. Je definována jako:
$$
y[n] = x[n] * h[n] = \sum_{k=-\infty}^{\infty} x[k] \cdot h[n - k]$$
Význam konvoluce spočívá v tom, že umožňuje zjistit, jak LTI systém reaguje na různé vstupní signály. 
Je komutativitu, asociativitu a distributivitu.

## Lekce 2
### Jak se řeší diferenční rovnice – popište proces, cíl a známé metody.

Diferenční rovnice se řeší pomocí různých metod, jako jsou metoda charakteristické rovnice, metoda zpožděných funkcí nebo metoda záměny proměnných. Cílem je najít obecné řešení, které zahrnuje homogenní a partikulární řešení.

### Co je autokorelace a křížová korelace deterministických signálů (význam, vlastnosti)?

Korelace je měření podobnosti mezi dvěma signály. Autokorelace měří podobnost signálu sám se sebou v různých časových posunech, zatímco křížová korelace měří podobnost mezi dvěma různými signály.
### Co je energie a výkon signálu (význam, výpočet)?

Energie signálu je celková energie, kterou signál obsahuje, a je definována jako součet čtverců amplitud signálu v čase, vyjadřuje "aktivitu/velikost". Výkon signálu je průměrná energie na jednotku času a je definován jako energie dělená časem.
### Co je diskrétní Fourierova transformace (DTFT) – notace, vlastnosti?
Diskrétní Fourierova transformace (DTFT) je matematická transformace, která převádí diskrétní signál z časové oblasti do frekvenční oblasti. Notace je obvykle vyjádřena jako:
$$
X(e^{j\omega}) = \sum_{n=-\infty}^{\infty} x[n] e^{-j\omega n}$$
DTFT má vlastnosti jako linearita, periodicita a symetrie.
Je důležitá pro analýzu frekvenčního obsahu diskrétních signálů.

### Co je spektrum DTFT signálu (význam, vlastnosti)?

Spektrum DTFT signálu je reprezentace signálu v frekvenční oblasti, která ukazuje, jaké frekvence jsou přítomny v signálu a s jakou amplitudou. Vlastnosti zahrnují periodicitu (s periodou $2\pi$), symetrii (pro reálné signály) a linearitu.

## Lekce 3
### Co znamená digitální frekvence v kontextu DTFT spektra?
Digitální frekvence v kontextu DTFT spektra je měřítko frekvence v jednotkách vzorkovací frekvence. Je definována jako $\omega = 2\pi f / f_s$, kde $f$ je analogová frekvence a $f_s$ je vzorkovací frekvence.
### Co je frekvenční odezva (význam, notace, periodicita, symetrie)?
Frekvenční odezva LTI systému je popis, jak systém reaguje na různé frekvence vstupního signálu. Notace je obvykle vyjádřena jako $H(e^{j\omega})$, kde $\omega$ je digitální frekvence. Frekvenční odezva je periodická s periodou $2\pi$ a může mít symetrii v závislosti na tom, zda je systém reálný nebo komplexní.
### Jaká je odezva LTI systému na signál (model pomocí diferenční rovnice – LCCDE, impulsní odezva – IR, frekvenční odezva – FR)?
LCCDE popisuje vztah mezi vstupem a výstupem pomocí diferenčních rovnic, IR je reakce systému na jednotkový impuls a FR popisuje, jak systém reaguje na různé frekvence.

### Jaké jsou vztahy mezi modely LTI systému (LCCDE → IR, LCCDE → FR, IR → FR)?

LCCDE lze převést na impulsní odezvu (IR) pomocí řešení diferenční rovnice. IR lze poté použít k výpočtu frekvenční odezvy (FR) pomocí DTFT. Naopak, pokud známe FR, můžeme získat IR pomocí inverzní DTFT. Vztahy jsou tedy:

- LCCDE → IR: Řešení diferenční rovnice poskytuje impulsní odezvu.
- LCCDE → FR: DTFT LCCDE poskytuje frekvenční odezvu.
- IR → FR: DTFT impulsní odezvy poskytuje frekvenční odezvu.
- FR → IR: Inverzní DTFT frekvenční odezvy poskytuje impulsní odezvu.
- IR → LCCDE: Impulsní odezva lze použít k sestavení diferenční rovnice.
- FR → LCCDE: Frekvenční odezva lze použít k sestavení diferenční rovnice pomocí inverzní DTFT.

### Jak řešit LCCDE pomocí DTFT?

LCCDE lze řešit pomocí DTFT tím, že převedeme diferenční rovnici do frekvenční oblasti. To zahrnuje aplikaci DTFT na obě strany rovnice, což umožňuje převést diferenciální operace na algebraické operace. Výsledkem je algebraická rovnice, kterou lze snadno vyřešit pro frekvenční odezvu. Poté můžeme použít inverzní DTFT k získání časové odezvy systému.

### Jak konvolvovat signály s nekonečným trváním?

Pomocí kruhové konvoluce.

## Lekce 4

### Co je LTI systém s lineární fází (notace, vlastnosti)?
LTI systém s lineární fází je systém, jehož frekvenční odezva má konstantní fázový posun pro všechny frekvence. Notace pro LTI systém s lineární fází zahrnuje $H(e^{j\omega}) = |H(e^{j\omega})| e^{j\phi(\omega)}$, kde $\phi(\omega)$ je lineární funkce frekvence. Vlastnosti zahrnují:

### Jaké jsou způsoby zapojení systémů (sériové, paralelní)?
### Co je poměr signál/šum (definice, decibely)?

## Lekce 5
### Co je vzorkování (vztah mezi analogovou a digitální frekvencí/spektrem, vzorkovací teorém – Nyquist, aliasing)?
### Jak se mění vzorkovací frekvence (decilace, interpolace, změna racionálním faktorem)?
### Co je diskrétní Fourierova transformace (DFT) – vztah k DTFT, notace?

## Lekce 6
### Jaké jsou vlastnosti DFT (linearita, symetrie, periodicita, frekvenční rozlišení)?
### Co je kruhová konvoluce (význam, výpočet lineární konvoluce pomocí kruhové)?
### Jak funguje lineární konvoluce pomocí overlap-add (motivace, základní implementace, využití FFT)?
### Co je rychlá Fourierova transformace (FFT)?

## Lekce 7
### Jaký je vztah periodicity signálu a jeho spektra DFT?
### Co je krátkodobá spektrální analýza (motivace, princip, spektrogram)?
### Co je okno (vlastnosti v časové oblasti, hlavní parametry ve frekvenční oblasti)?
### Co je harmonická spektrální analýza (definice, rozlišitelnost spektrálních složek, vliv oknování)?

## Lekce 8
### Jaký je základní model hudebního tónu (základní parametry a jejich význam)?
### Jak se detekuje komplex QRS v EKG, jaký je algoritmus a význam jednotlivých kroků?
### Jak funguje potlačení šumu v řeči pomocí spektrálního prahování a spektrální subtrakce (předpoklady o šumu, význam jednotlivých kroků)?

## Lekce 9
### Co je Z-transformace (definice, vztah k DTFT, linearita, konvoluční teorém)?
### Co je systémová (přenosová) funkce LTI systému (význam, notace, nuly a póly)?
### Jak se provádí inverzní Z-transformace (polynomiální dělení, rozklad na parciální zlomky)?

## Lekce 10
### Jak analyzovat LTI systém pomocí Z-transformace (stabilita, kauzalita, realizovatelnost)?
### Co je inverzní systém?
### Co je systém s minimální fází (definice, motivace)?
### Jaké jsou modely LTI systému a jejich vztahy (LCCDE, frekvenční odezva, přenosová funkce, impulsní odezva)?

## Lekce 11
### Jaké jsou vlastnosti filtrů (stabilita, kauzalita, reálné koeficienty, lineární fáze, frakcionální zpoždění)?
### Jaké jsou specifikace filtrů (parametry)?
### Jak navrhnout notch filtry (princip, FIR/IIR varianty a jejich vlastnosti)?
### Co je ideální frekvenčně selektivní filtr (proč není prakticky realizovatelný)?
### Jak funguje metoda oknování pro návrh FIR filtrů (princip, výběr parametrů)?

## Lekce 12
### Jak navrhnout FIR filtr pomocí optimalizačních kritérií (filtry nejmenších čtverců, filtry typu equiripple – výhody oproti metodě oknování)?
### Jaké jsou základní typy IIR filtrů (vlastnosti amplitudové odezvy)?
### Jak porovnat IIR a FIR filtry (stabilita, výpočetní náročnost, zpoždění, fázové zkreslení)?

## Lekce 13
### Co je optimální filtr?
### Jak se liší od frekvenčně selektivních filtrů?
### Jak se navrhuje optimální filtr metodou nejmenších čtverců (kritérium, příklad)?
