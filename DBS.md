# Řízení databází

## 1. Historie a modely databází

- Od souborových systémů (redundance, nekonzistence) → SŘBD (Systém Řízení Báze Dat)
- ANSI-SPARC 1975: 3-úrovňová architektura (interní, konceptuální, externí)
- Modely:
  - **Hierarchický, síťový** – záznamově orientované
  - **Relační** (E.F. Codd, 1970) – na základě množinové matematiky
  - **Objektově-orientovaný (OODBMS)**
  - **Objektově-relační (ORDBMS)** – mix relačního a OO modelu
  - **NoSQL** – dokumentové, grafové, key-value, sloupcové
  - **NewSQL** – moderní SŘBD s SQL a ACID vlastnostmi

---

## 2. Relační model dat a integrita

- **Relace**: podmnožina kartézského součinu domén
- **Schéma relace**: R(A1:D1, ..., An:Dn)
- **Primární klíč** – jednoznačná identifikace n-tice
- **Cizí klíč** – referenční integrita mezi tabulkami
- Relace nesmí obsahovat duplicity
  Základní operace:
  - sjednotit
  - kartézský součin
  - rozdíl
  - selekce
  - projekce
  - přejmenování

---

## 3. Normalizace a návrh schémat

- **1NF** – atomické hodnoty
- **Funkční závislosti** – B → C
- **Kandidátní klíč** – minimální množina určující n-tici
- **3NF** – neklíčové atributy nesmí záviset na jiných neklíčových
- **BCNF** – determinant každé závislosti musí být klíčem
- **Dekompozice** – bezztrátová a s pokrytím závislostí
- **Armstrongova pravidla** – pro odvozování závislostí

---

## 4. Transakce a ACID

- **Transakce**: série operací nad DB
- **ACID** vlastnosti:
  - **Atomicity** – proběhne vše nebo nic
  - **Consistency** – zachování konzistence
  - **Isolation** – nezávislost transakcí
  - **Durability** – trvalost potvrzených změn

---

## 5. Souběžné zpracování a izolace

- Konflikty:
  - WR – čtení nekompletních dat
  - RW – neopakovatelná čtení
  - WW – přepisování nekompletních dat
- Řízení zámků:
  - **2PL**, **Strict 2PL**
  - **Deadlock detection/prevention**
- **Izolační úrovně SQL**:
  - `READ UNCOMMITTED` → možné "dirty reads"
  - `READ COMMITTED` → zabránění dirty reads
  - `REPEATABLE READ` → zabránění unrepeatable reads
  - `SERIALIZABLE` → nejvyšší izolace

---

## 6. Zotavení (Recovery)

- **ARIES** – analýza, REDO, UNDO
- **Write-ahead logging (WAL)** – nejprve log, pak zápis
- **LSN (Log Sequence Number)** – sledování změn
- Využití žurnálů pro návrat do konzistentního stavu

---

## 7. Indexování a optimalizace

- **Typy indexů**:
  - **Primární** vs. **sekundární**
  - **Clustered** vs. **Unclustered**
  - **Dense** vs. **Sparse**
- **Struktury**:
  - **ISAM**, **B+ stromy** (pro rozsahové dotazy)
  - **Hash** (statický, lineární, extendible)
  - **Bitmapové** (Oracle, vhodné pro malou kardinalitu)
- **Optimalizace dotazů** – přepis do relační algebry, odhad nákladů

---

## 8. NoSQL a alternativní modely

- **NoSQL** – bez pevného schématu, horizontální škálování, nepoužívá se JOIN
- Typy: dokumentové, grafové, sloupcové, key-value
- **CAP teorém** – konzistence, dostupnost, tolerance vůči síťovému rozdělení

---

## 9. Dotazovací jazyky

- **SQL** – DML, DDL, DCL, TCL
- **Transakce v SQL** – BEGIN, COMMIT, ROLLBACK
- **Programování** – procedury, triggery (spouště), ORM (Hibernate, Spring)

---

## 10. Slovník pojmů

| Pojem                 | Význam |
|-----------------------|--------|
| SŘBD                 | Systém řízení báze dat (např. PostgreSQL, Oracle) |
| Relační model        | Model dat založený na relacích a množinách |
| Normalizace          | Proces rozkladu tabulek za účelem odstranění redundance |
| 1NF, 3NF, BCNF        | Normální formy databází podle úrovně eliminace závislostí |
| Funkční závislost    | Závislost jedné množiny atributů na druhé |
| Transakce            | Sada databázových operací s vlastnostmi ACID |
| ACID                 | Atomicity, Consistency, Isolation, Durability |
| Index                | Datová struktura pro rychlé vyhledávání |
| B+ strom             | Vyhledávací strom vhodný pro rozsahové dotazy |
| Hash index           | Vhodný pro rovnostní porovnání |
| NoSQL                | Alternativa k relačním DBMS pro velká, nestrukturovaná data |
| ORM                  | Objektově-relační mapování (např. Hibernate) |
| WAL                  | Write-Ahead Logging, technika zotavení |

---

*Zpracováno ze slidů přednášek Ing. Romana Špánka, Ph.D., Technická univerzita v Liberci.*
