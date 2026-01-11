# Partikuläre Lösungen bei inhomogenen linearen ODEs 1. Ordnung

## Übersicht: Ansätze für verschiedene Störfunktionen

| Nr. | Differentialgleichung (DGL) | Homogene Lösung ($y_h$) | Störfunktion $f(x)$ | Ansatz Partikuläre Lösung ($y_p$) |
|-----|---------------------------|------------------------|-------------------|----------------------------------|
| 1 | $y' - 2y = 5x^2$ | $C \cdot e^{2x}$ | $5x^2$ | $Ax^2 + Bx + C$ |
| 2 | $2y' + 3y = 5x^2$ | $C \cdot e^{-1.5x}$ | $2.5x^2$ | $Ax^2 + Bx + C$ |
| 3 | $3y' + 5y - x = 0$ | $C \cdot e^{-\frac{5}{3}x}$ | $\frac{1}{3}x$ | $Ax + B$ |
| 4 | $y' - 5y = \sin(-3x)$ | $C \cdot e^{5x}$ | $\sin(-3x)$ | $A \cdot \sin(-3x) + B \cdot \cos(-3x)$ |
| 5 | $y' + y = \cos(4x)$ | $C \cdot e^{-x}$ | $\cos(4x)$ | $A \cdot \sin(4x) + B \cdot \cos(4x)$ |
| 6 | $y' + 2y = 5e^{3x}$ | $C \cdot e^{-2x}$ | $5e^{3x}$ | $A \cdot e^{3x}$ |
| 7 | $y' - 3y = e^{3x}$ | $C \cdot e^{3x}$ | $e^{3x}$ | $A \cdot x \cdot e^{3x}$ **(Resonanzfall!)** |

---

## Beispiel 1: Polynom als Störfunktion
**DGL:** $y' - 2y = 5x^2$

**Schritt 1 - Homogene Lösung:**
$$y' - 2y = 0 \implies y_h = C \cdot e^{2x}$$

**Schritt 2 - Ansatz für partikuläre Lösung:**
Störfunktion ist Polynom 2. Grades → Ansatz: $y_p = Ax^2 + Bx + C$

**Schritt 3 - Ableitung und Einsetzen:**
$$y_p' = 2Ax + B$$
$$2Ax + B - 2(Ax^2 + Bx + C) = 5x^2$$
$$2Ax + B - 2Ax^2 - 2Bx - 2C = 5x^2$$
$$-2Ax^2 + (2A - 2B)x + (B - 2C) = 5x^2$$

**Schritt 4 - Koeffizientenvergleich:**
- $x^2$: $-2A = 5 \implies A = -\frac{5}{2}$
- $x^1$: $2A - 2B = 0 \implies 2(-\frac{5}{2}) - 2B = 0 \implies B = -\frac{5}{2}$
- $x^0$: $B - 2C = 0 \implies -\frac{5}{2} - 2C = 0 \implies C = -\frac{5}{4}$

**Partikuläre Lösung:** $y_p = -\frac{5}{2}x^2 - \frac{5}{2}x - \frac{5}{4}$

**Gesamtlösung:** 
$$\boxed{y = C \cdot e^{2x} - \frac{5}{2}x^2 - \frac{5}{2}x - \frac{5}{4}}$$

---

## Beispiel 4: Sinus als Störfunktion
**DGL:** $y' - 5y = \sin(-3x)$

**Schritt 1 - Homogene Lösung:**
$$y' - 5y = 0 \implies y_h = C \cdot e^{5x}$$

**Schritt 2 - Ansatz für partikuläre Lösung:**
Störfunktion ist Sinus → Ansatz: $y_p = A \sin(-3x) + B \cos(-3x)$

**Schritt 3 - Ableitung und Einsetzen:**
$$y_p' = -3A \cos(-3x) + 3B \sin(-3x)$$
$$-3A \cos(-3x) + 3B \sin(-3x) - 5[A \sin(-3x) + B \cos(-3x)] = \sin(-3x)$$
$$-3A \cos(-3x) + 3B \sin(-3x) - 5A \sin(-3x) - 5B \cos(-3x) = \sin(-3x)$$
$$(3B - 5A) \sin(-3x) + (-3A - 5B) \cos(-3x) = \sin(-3x)$$

**Schritt 4 - Koeffizientenvergleich:**
- $\sin(-3x)$: $3B - 5A = 1$
- $\cos(-3x)$: $-3A - 5B = 0 \implies 3A = -5B \implies A = -\frac{5B}{3}$

Einsetzen in erste Gleichung:
$$3B - 5(-\frac{5B}{3}) = 1$$
$$3B + \frac{25B}{3} = 1$$
$$\frac{9B + 25B}{3} = 1$$
$$34B = 3 \implies B = \frac{3}{34}$$

$$A = -\frac{5 \cdot 3}{3 \cdot 34} = -\frac{5}{34}$$

**Partikuläre Lösung:** $y_p = -\frac{5}{34} \sin(-3x) + \frac{3}{34} \cos(-3x)$

**Gesamtlösung:** 
$$\boxed{y = C \cdot e^{5x} - \frac{5}{34} \sin(-3x) + \frac{3}{34} \cos(-3x)}$$

---

## Beispiel 6: Exponentialfunktion als Störfunktion
**DGL:** $y' + 2y = 5e^{3x}$

**Schritt 1 - Homogene Lösung:**
$$y' + 2y = 0 \implies y_h = C \cdot e^{-2x}$$

**Schritt 2 - Ansatz für partikuläre Lösung:**
Störfunktion ist $e^{3x}$ → Ansatz: $y_p = A \cdot e^{3x}$

**Prüfung:** $e^{3x}$ ist **nicht** Teil der homogenen Lösung (Exponent anders!) → normaler Ansatz OK

**Schritt 3 - Ableitung und Einsetzen:**
$$y_p' = 3A \cdot e^{3x}$$
$$3A \cdot e^{3x} + 2A \cdot e^{3x} = 5e^{3x}$$
$$5A \cdot e^{3x} = 5e^{3x}$$

**Schritt 4 - Koeffizienten bestimmen:**
$$5A = 5 \implies A = 1$$

**Partikuläre Lösung:** $y_p = e^{3x}$

**Gesamtlösung:** 
$$\boxed{y = C \cdot e^{-2x} + e^{3x}}$$

**Erklärung:** Das war einfach, weil der Exponent der Störfunktion (3) verschieden vom Exponenten der homogenen Lösung (-2) ist.

---

## Beispiel 7: Resonanzfall! 🔴
**DGL:** $y' - 3y = e^{3x}$

**Schritt 1 - Homogene Lösung:**
$$y' - 3y = 0 \implies y_h = C \cdot e^{3x}$$

**Schritt 2 - Ansatz für partikuläre Lösung:**
Störfunktion ist $e^{3x}$ → **ABER:** Das ist **exakt** die homogene Lösung!

**Resonanzfall!** Normaler Ansatz $y_p = A \cdot e^{3x}$ funktioniert **NICHT**!

**Richtiger Ansatz:** $y_p = A \cdot x \cdot e^{3x}$ (mit zusätzlichem Faktor $x$)

**Schritt 3 - Ableitung und Einsetzen:**
$$y_p' = A \cdot e^{3x} + A \cdot x \cdot 3e^{3x} = Ae^{3x}(1 + 3x)$$
$$Ae^{3x}(1 + 3x) - 3 \cdot Axe^{3x} = e^{3x}$$
$$Ae^{3x} + 3Axe^{3x} - 3Axe^{3x} = e^{3x}$$
$$Ae^{3x} = e^{3x}$$

**Schritt 4 - Koeffizienten bestimmen:**
$$A = 1$$

**Partikuläre Lösung:** $y_p = x \cdot e^{3x}$

**Gesamtlösung:** 
$$\boxed{y = C \cdot e^{3x} + x \cdot e^{3x} = e^{3x}(C + x)}$$

**Erklärung:** 
- **Resonanzfall** tritt auf, wenn die Störfunktion dieselbe Form wie die homogene Lösung hat
- Dann muss man den Ansatz mit $x$ multiplizieren: $y_p = x \cdot (\text{normaler Ansatz})$
- Das ist wie bei erzwungenen Schwingungen - wenn die Anregungsfrequenz = Eigenfrequenz ist!

---

## Allgemeine Ansätze - Cheat Sheet

| Störfunktion $f(x)$ | Normaler Ansatz $y_p$ | Resonanzfall-Ansatz |
|---------------------|----------------------|---------------------|
| $Polynom \, n$-ten Grades | $A_nx^n + ... + A_1x + A_0$ | $x \cdot (\text{Polynom})$ |
| $e^{\alpha x}$ | $A \cdot e^{\alpha x}$ | $A \cdot x \cdot e^{\alpha x}$ |
| $\sin(\omega x)$ oder $\cos(\omega x)$ | $A \sin(\omega x) + B \cos(\omega x)$ | $x(A \sin(\omega x) + B \cos(\omega x))$ |
| $e^{\alpha x} \cdot \sin(\omega x)$ | $e^{\alpha x}(A \sin(\omega x) + B \cos(\omega x))$ | $x \cdot e^{\alpha x}(A \sin(\omega x) + B \cos(\omega x))$ |

**Wann Resonanzfall?**
- Wenn der Ansatz **bereits in der homogenen Lösung enthalten ist**
- Dann: Ansatz mit $x$ multiplizieren!
