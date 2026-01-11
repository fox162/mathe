# ODE (Ordinary Differential Equations)
gleichung mit ableitung drinnen.

## Beispiel
$y' = y$

$\frac{dy}{dx} = x + y$

---

## ODEs aus Textaufgaben aufstellen

**Wie geht man vor?**

1. **Variablen identifizieren** - Was ändert sich? (z.B. Temperatur, Anzahl, Masse)
2. **Änderungsrate beschreiben** - Ableitung der Variable (z.B. $\frac{dT}{dt}$)
3. **Schlüsselwörter übersetzen:**
   - "proportional zu" → $k \cdot (\text{etwas})$
   - "wächst/steigt" → positiv
   - "fällt/zerfällt" → negativ
   - "Unterschied/Differenz" → Subtraktion
4. **Anfangsbedingungen** angeben (z.B. $y(0) = y_0$)

**Typische Anwendungen:**
- Wachstumsprozesse (Bakterien, Bevölkerung)
- Zerfallsprozesse (Radioaktivität, Medikamente)
- Abkühlungs-/Erwärmungsprozesse (Newtonsches Abkühlungsgesetz)
- Mechanik (Bewegung mit Reibung, freier Fall)

### [Beispiele zum Aufstellen von ODEs](./bsp-aufstellen.md)

---

### Notation
*Namen sind egal*
| Name     | Leibniz                                      | Strich (Lagrange)   | Punkt (Newton) |
|----------|----------------------------------------------|---------------------|---------------|
|          | $\frac{dy}{dx} = f(x,y)$                     | $y' = f(x,y)$       | $\dot{y} = f(t,y)$ |
| 2. Ableitung | $\frac{d^2y}{dx^2} = f(x,y,y')$         | $y'' = f(x,y,y')$     | $\ddot{y} = f(t,y,\dot{y})$ |
| Beispiel | $\frac{d^2y}{dx^2} + 2\frac{dy}{dx} + y = 0$ | $y'' + 2y' + y = 0$ |
| Hinweis  | **Achtung:** $\frac{d^2y}{dx^2} \neq \frac{dy^2}{d^2x}$<br>(links = zweite Ableitung,<br>rechts = keine Standardnotation) | $y^{(4)} = y''''$<br>$y^{(4)} \neq y^4$<br>$y''^3=(y'')^3$ |

### Charakteristika
$gl1: y^{(4)}+3 \cdot y^2 \cdot y''^3-8 \cdot y' \cdot x +2 \cdot y^2 \cdot sin(x) = e^{-x}$

|            | Ordnung           | Grad                     |
| ---------- | ----------------- | ------------------------ |
| Definition | höchste Ableitung | höchste potenz           |
| gl1        | **4**             | **5** ($y^2\cdot y''^3$) |


### Lineare/Nichtlineare ODE
|            | Linear                                        | Nichtlinear     |
|------------|-----------------------------------------------|-----------------|
| Definition | gesuchte Funktion und Ableitung nur 1. Potenz | alles andere    |
| Beispiel   | $m \cdot y'' + r \cdot y'+k \cdot y=x^2$      | $ y'^2 + y = 0 $|


### Homogene/Inhomogene ODE
|            | Homogen                                        | Inhomogen     |
|------------|------------------------------------------------|---------------|
| Definition | rechte Seite = 0<br>(keine "Störfunktion")    | rechte Seite ≠ 0<br>(mit "Störfunktion") |
| Form       | $a_n \cdot y^{(n)} + ... + a_1 \cdot y' + a_0 \cdot y = 0$ | $a_n \cdot y^{(n)} + ... + a_1 \cdot y' + a_0 \cdot y = g(x)$ |
| Beispiel   | $y'' + 2y' + y = 0$                            | $y'' + 2y' + y = e^x$ |

**Wichtig:** Die Lösung einer inhomogenen linearen ODE setzt sich zusammen aus:
- **Homogene Lösung** $y_h$ (Lösung der zugehörigen homogenen Gleichung)
- **Partikuläre Lösung** $y_p$ (eine spezielle Lösung der inhomogenen Gleichung)
- **Gesamtlösung:** $y = y_h + y_p$


### Explizite/Implizite ODE
|            | Explizit                                       | Implizit     |
|------------|------------------------------------------------|---------------|
| Definition | höchste Ableitung ist isoliert<br>(freigestellt) | höchste Ableitung ist nicht isoliert |
| Form       | $y^{(n)} = f(x, y, y', ..., y^{(n-1)})$        | $F(x, y, y', ..., y^{(n)}) = 0$ |
| Beispiel   | $y' = x + y$<br>$y'' = 2x - 3y'$              | $y'^2 + y = 0$<br>$(y')^3 + xy = e^x$ |
| Vorteil    | einfacher lösbar<br>(numerische Methoden anwendbar) | allgemeiner<br>(realistischere Modelle) |


### Autonome/Nichautonome ODE
|            | Autonom                                        | Nichautonom     |
|------------|------------------------------------------------|---------------|
| Definition | $x$ kommt nicht explizit vor<br>(nur $y$ und Ableitungen) | $x$ kommt explizit vor |
| Form       | $y' = f(y)$                                    | $y' = f(x, y)$ |
| Beispiel   | $y' = y^2$<br>$y'' + 2y' + y = 0$              | $y' = x + y$<br>$y'' + xy' + y = \sin(x)$ |
| Spezialfall| Systeme sind unabhängig von Zeit              | Systeme hängen von Zeit ab |


### Wichtige Begriffe
| Begriff          | Bedeutung                                      | Beispiel |
|------------------|------------------------------------------------|----------|
| **Störfunktion** | $g(x)$ auf der rechten Seite einer inhomogenen ODE<br>(term nur mit $x$, ohne $y$ und Ableitungen) | In $y'' + 2y' + y = \sin(x)$ ist $\sin(x)$ die Störfunktion |
| **Anfangsbedingungen** | werte für $y$ und evtl. ableitungen bei $x=x_0$<br>(bestimmen die integrationskonst.) | $y(0) = 1, y'(0) = 0$ |
| **Randwertproblem** | werte von $y$ an mehreren stellen vorgegeben<br>(z.B. anfang und ende) | $y(0) = 1, y(1) = 2$ |
| **Anfangswertproblem** | anfangsbedingung(en) gegeben<br>(bestimmt eindeutige lösung) | ODE + $y(x_0) = y_0$ |
| **Partikulärlösung** | spezielle lösung der inhomogenen gleichung<br>(erfüllt die ganze gleichung) | $y_p$ bei $y'' + 2y' + y = e^x$ |
| **Allgemeine Lösung** | $y = y_h + y_p$<br>(enthält alle lösungen mit integrationskonstanten) | $y = Ce^{-x} + y_p$ |
| **Charakteristische Gleichung** | polynom das man aus homogener ODE erhält<br>(für lösungsansatz $y = e^{\lambda x}$) | Aus $y'' + 2y' + y = 0$: $\lambda^2 + 2\lambda + 1 = 0$ |


---

## Lösungsverfahren für lineare ODEs
### Trennung der Variablen (wichtig)

#### Wann kann man das machen?
Diese Methode funktioniert nur bei **separierbaren ODEs**:
- Die ODE muss 1. Ordnung sein: $y' = ...$
- Die ODE muss sich in der Form $y' = f(x) \cdot g(y)$ schreiben lassen
- Das heißt: rechte Seite ist ein **Produkt** von einer Funktion nur mit $x$ und einer Funktion nur mit $y$

| Separierbar? | Beispiel |
|---|---|
| ✅ JA | $y' = x \cdot y$ (weil $= x \cdot y = f(x) \cdot g(y)$) |
| ✅ JA | $y' = \frac{x}{y}$ (weil $= \frac{1}{y} \cdot x = g(y) \cdot f(x)$) |
| ❌ NEIN | $y' = x + y$ (weil es eine **Summe** ist, nicht Produkt) |
| ❌ NEIN | $y'' + y' = 0$ (weil es 2. Ordnung ist) |

#### Verfahren (Schritt für Schritt)
1. **aufschreiben** die ODE in der Form: $y' = f(x) \cdot g(y)$
2. **umschreib** mit $\frac{dy}{dx} = f(x) \cdot g(y)$
3. **Trennen der Variablen:** $\frac{dy}{g(y)} = f(x) \, dx$
4. **Integrieren beider Seiten:** $\int \frac{dy}{g(y)} = \int f(x) \, dx$
5. **Lösen nach $y$** (wenn möglich)

### [Beispiele](./bsp-trennen.md)

---

## Homogene Lösung finden (für lineare ODEs 1. Ordnung)

**Was ist die homogene Gleichung?**
Aus der inhomogenen linearen ODE $y' + a \cdot y = f(x)$ wird die homogene Gleichung:
$$y' + a \cdot y = 0$$
(einfach die Störfunktion $f(x)$ weglassen)

### Methode 1: Trennung der Variablen (same shit as before)
**Für konstante Koeffizienten:** $y' + ay = 0$

**Schritt 1:** Umschreiben: $\frac{dy}{dx} = -ay$

**Schritt 2:** Trennung: $\frac{dy}{y} = -a \, dx$

**Schritt 3:** Integrieren:
$$\int \frac{dy}{y} = \int -a \, dx$$
$$\ln|y| = -ax + K$$

**Schritt 4:** Nach $y$ auflösen:
$$y = e^{-ax + K} = e^K \cdot e^{-ax}$$

**Homogene Lösung:** $\boxed{y_h = C \cdot e^{-ax}}$ (wobei $C = \pm e^K$)

### Methode 2: Charakteristischer Ansatz (schneller!)
**Für konstante Koeffizienten:** $y' + ay = 0$

**Ansatz:** $y = e^{\lambda x}$ (versuche Exponentialfunktion)

**Ableitung:** $y' = \lambda e^{\lambda x}$

**Einsetzen in DGL:**
$$\lambda e^{\lambda x} + a \cdot e^{\lambda x} = 0$$
$$e^{\lambda x}(\lambda + a) = 0$$

Da $e^{\lambda x} \neq 0$:
$$\lambda + a = 0 \implies \lambda = -a$$

**Homogene Lösung:** $\boxed{y_h = C \cdot e^{-ax}}$

### methode 3 (einfach das verwenden wenns geht)
**Bei** $y' + ay = 0$

einfach $a$ nehmen und bei $y_h = C \cdot e^{-ax}$ einsetzen.

**Homogene Lösung:** $\boxed{y_h = C \cdot e^{-ax}}$

lol

**WICHTIG wenn**

$ny' + ay = f(x)$

dann erst durch $n$ teilen:

$y' + \frac{a}{n}y = \frac{f(x)}{n}$

**beispiel:**

$2y' + 3y = 5x^2$

$\Rightarrow y' + \frac{3}{2}y = \frac{5x^2}{2}$

dann $a = \frac{3}{2}$ in

$y_h = C \cdot e^{-ax}$

einsetzen.

$\Rightarrow y_h = C \cdot e^{-\frac{3}{2}x}=C \cdot e^{-1.5x}$



### Beispiele: Homogene Lösung bestimmen

| DGL | Homogene Form | $\lambda$ | $y_h$ |
|-----|---------------|-----------|-------|
| $y' - 2y = 5x^2$ | $y' - 2y = 0$ | $\lambda - 2 = 0 \implies \lambda = 2$ | $C \cdot e^{2x}$ |
| $y' + 3y = \cos(x)$ | $y' + 3y = 0$ | $\lambda + 3 = 0 \implies \lambda = -3$ | $C \cdot e^{-3x}$ |
| $2y' + 3y = 5x^2$ | $2y' + 3y = 0$ <br> bzw. $y' + \frac{3}{2}y = 0$ | $\lambda + \frac{3}{2} = 0 \implies \lambda = -\frac{3}{2}$ | $C \cdot e^{-1.5x}$ |
| $y' - 5y = \sin(x)$ | $y' - 5y = 0$ | $\lambda - 5 = 0 \implies \lambda = 5$ | $C \cdot e^{5x}$ |

**Merke:** 
- Bei $y' + ay = 0$ ist $y_h = C \cdot e^{-ax}$
- Bei $y' - ay = 0$ ist $y_h = C \cdot e^{ax}$ (Vorzeichen beachten!)

---

## Ansatz vom Typ der rechten Seite (für inhomogene lineare ODEs)

**Was ist das?**
Bei **inhomogenen linearen ODEs** (z.B. $y' + ay = f(x)$) suchen wir die **Gesamtlösung** als:
$$y = y_h + y_p$$
- $y_h$ = homogene Lösung (setze $f(x) = 0$, siehe oben!)
- $y_p$ = partikuläre Lösung (eine spezielle Lösung der inhomogenen Gleichung)

**Wie findet man $y_p$?**
Der **Ansatz vom Typ der rechten Seite** bedeutet:
- Schaue dir die **Störfunktion** $f(x)$ an
- Wähle einen **Ansatz für $y_p$**, der die **gleiche Form** wie $f(x)$ hat
- Setze den Ansatz in die DGL ein und bestimme die Koeffizienten

**Wichtige Ansätze:**

| Störfunktion $f(x)$ | Ansatz für $y_p$ | Beispiel |
|---------------------|------------------|----------|
| Polynom $a_nx^n + ... + a_1x + a_0$ | $A_nx^n + ... + A_1x + A_0$ | $f(x) = 5x^2$ → $y_p = Ax^2 + Bx + C$ |
| $e^{\alpha x}$ | $A \cdot e^{\alpha x}$ | $f(x) = 5e^{3x}$ → $y_p = A \cdot e^{3x}$ |
| $\sin(\omega x)$ oder $\cos(\omega x)$ | $A \sin(\omega x) + B \cos(\omega x)$ | $f(x) = \cos(4x)$ → $y_p = A\sin(4x) + B\cos(4x)$ |
| $e^{\alpha x} \cdot P(x)$ | $e^{\alpha x} \cdot Q(x)$ | $f(x) = xe^{2x}$ → $y_p = (Ax+B)e^{2x}$ |

**⚠️ ACHTUNG - Resonanzfall:**
Wenn dein Ansatz **bereits in der homogenen Lösung $y_h$ vorkommt**, dann multipliziere den Ansatz mit $x$:
- Normal: $y_p = A \cdot e^{3x}$
- Resonanz: $y_p = A \cdot x \cdot e^{3x}$

**Vorgehen:**
1. Finde $y_h$ (löse homogene Gleichung)
2. Wähle Ansatz für $y_p$ basierend auf $f(x)$
3. Prüfe auf Resonanz (ist Ansatz ⊂ $y_h$?)
4. Setze $y_p$ in die DGL ein
5. Koeffizientenvergleich → bestimme $A, B, C, ...$
6. Gesamtlösung: $y = y_h + y_p$

### [Beispiele mit vollständigen Lösungen](07B-partikulaere-loesungen.md)
