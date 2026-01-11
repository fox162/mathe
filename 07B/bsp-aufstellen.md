# Beispiele: ODEs aus Textaufgaben aufstellen

## Beispiel 1: Newtonsches Abkühlungsgesetz 🌡️

**Aufgabe:**
Ein Körper wird aus dem Backofen bei 205°C in einen Raum mit Raumtemperatur 23°C gebracht.
Die Temperatur in Abhängigkeit von der Zeit fällt proportional zum Unterschied der Raumtemperatur zur Temperatur des Körpers.
Bestimme, welche der folgenden Differentialgleichungen den Temperaturänderungsprozess korrekt beschreibt.

### Schritt 1: Variablen definieren
- $T(t)$ = Temperatur des Körpers zur Zeit $t$ (in °C)
- $T_R = 23°C$ = Raumtemperatur (konstant)
- $t$ = Zeit (in Minuten oder Stunden)

### Schritt 2: Text analysieren
**"Die Temperatur ... fällt proportional zum Unterschied ..."**

Das bedeutet mathematisch:
- **Änderung der Temperatur** = $\frac{dT}{dt}$ oder $T'$
- **fällt** = negativ → Minus-Zeichen
- **proportional** = konstanter Faktor (z.B. $k$)
- **Unterschied** = $T(t) - T_R$ (Temperatur des Körpers minus Raumtemperatur)

### Schritt 3: ODE aufstellen
$$\frac{dT}{dt} = -k \cdot (T - T_R)$$

Mit $T_R = 23$:
$$\boxed{\frac{dT}{dt} = -k \cdot (T - 23)}$$

oder umgeformt:
$$\boxed{T' + kT = 23k}$$

### Schritt 4: Anfangsbedingung
$$T(0) = 205°C \quad \text{(Starttemperatur aus dem Backofen)}$$

### Schritt 5: Lösung der ODE (optional)

**Homogene Lösung:**
$$T' + kT = 0 \implies T_h = C \cdot e^{-kt}$$

**Partikuläre Lösung:**
Störfunktion: $23k$ (konstant)
Ansatz: $T_p = A$ (Konstante)
$$0 + kA = 23k \implies A = 23$$

**Gesamtlösung:**
$$T(t) = C \cdot e^{-kt} + 23$$

**Mit Anfangsbedingung:**
$$T(0) = 205: \quad C \cdot e^0 + 23 = 205$$
$$C = 182$$

**Endlösung:**
$$\boxed{T(t) = 182 \cdot e^{-kt} + 23}$$

**Interpretation:**
- Für $t \to \infty$: $T(t) \to 23°C$ (Körper erreicht Raumtemperatur)
- Je größer $k$, desto schneller die Abkühlung

---

## Beispiel 2: Exponentielles Wachstum 📈

**Aufgabe:**
Eine Bakterienkultur wächst proportional zur aktuellen Anzahl der Bakterien.

**Variablen:**
- $N(t)$ = Anzahl der Bakterien zur Zeit $t$
- $k$ = Wachstumsrate (konstant)

**Text analysieren:**
- "wächst proportional zur aktuellen Anzahl"
- Änderung = $\frac{dN}{dt}$
- proportional zu $N$

**ODE:**
$$\boxed{\frac{dN}{dt} = k \cdot N}$$
oder: $N' = kN$

**Lösung:**
$$N(t) = N_0 \cdot e^{kt}$$
wobei $N_0 = N(0)$ die Anfangspopulation ist.

---

## Beispiel 3: Radioaktiver Zerfall ☢️

**Aufgabe:**
Die Zerfallsgeschwindigkeit einer radioaktiven Substanz ist proportional zur vorhandenen Menge.

**Variablen:**
- $m(t)$ = Masse der Substanz zur Zeit $t$
- $\lambda$ = Zerfallskonstante

**Text analysieren:**
- "Zerfallsgeschwindigkeit" = $\frac{dm}{dt}$
- "proportional zur vorhandenen Menge" = $\lambda \cdot m$
- Da es ein **Zerfall** ist: negativ!

**ODE:**
$$\boxed{\frac{dm}{dt} = -\lambda \cdot m}$$

**Lösung:**
$$m(t) = m_0 \cdot e^{-\lambda t}$$

**Halbwertszeit $T_{1/2}$:**
$$m(T_{1/2}) = \frac{m_0}{2} \implies e^{-\lambda T_{1/2}} = \frac{1}{2}$$
$$T_{1/2} = \frac{\ln(2)}{\lambda}$$

---

## Beispiel 4: Fallender Körper mit Luftwiderstand 🪂

**Aufgabe:**
Ein Körper fällt unter dem Einfluss der Schwerkraft. Der Luftwiderstand ist proportional zur Geschwindigkeit.

**Variablen:**
- $v(t)$ = Geschwindigkeit zur Zeit $t$
- $g$ = Erdbeschleunigung (ca. 9.81 m/s²)
- $k$ = Luftwiderstandskoeffizient

**Kräfte:**
- Schwerkraft: $F_g = mg$ (nach unten)
- Luftwiderstand: $F_L = kv$ (nach oben, bremst)

**Newton: $F = ma = m\frac{dv}{dt}$**
$$m\frac{dv}{dt} = mg - kv$$

**ODE:**
$$\boxed{\frac{dv}{dt} = g - \frac{k}{m}v}$$

**Grenzgeschwindigkeit** (für $\frac{dv}{dt} = 0$):
$$v_\infty = \frac{mg}{k}$$

---

## Beispiel 5: Mischungsproblem 🧪

**Aufgabe:**
Ein Tank enthält 100 L Wasser. Eine Salzlösung mit Konzentration 0.5 kg/L fließt mit 3 L/min hinein.
Die gut durchmischte Lösung fließt mit der gleichen Rate wieder heraus.

**Variablen:**
- $S(t)$ = Salzmenge im Tank zur Zeit $t$ (in kg)
- $V = 100$ L (Volumen konstant)

**Änderung:**
$$\frac{dS}{dt} = \text{Zufluss} - \text{Abfluss}$$

**Zufluss:** 
$$3 \, \text{L/min} \cdot 0.5 \, \text{kg/L} = 1.5 \, \text{kg/min}$$

**Abfluss:**
- Konzentration im Tank: $\frac{S(t)}{100}$ kg/L
- Abfluss: $3 \, \text{L/min} \cdot \frac{S(t)}{100} = \frac{3S}{100}$ kg/min

**ODE:**
$$\boxed{\frac{dS}{dt} = 1.5 - \frac{3S}{100}}$$

oder:
$$\boxed{\frac{dS}{dt} + \frac{3}{100}S = 1.5}$$

---

## Tipps zum Aufstellen von ODEs

1. **Variablen klar definieren** (z.B. $y(t)$, nicht nur $y$)
2. **Schlüsselwörter identifizieren:**
   - "proportional" → $k \cdot (\text{etwas})$
   - "Änderung", "Wachstum" → $\frac{dy}{dt}$
   - "fällt", "Zerfall" → Minus-Zeichen
3. **Einheiten prüfen:** Beide Seiten müssen gleiche Einheit haben
4. **Anfangsbedingungen** nicht vergessen: $y(t_0) = y_0$
5. **Physikalische Gesetze nutzen:**
   - Newton: $F = ma$
   - Erhaltungssätze (Masse, Energie)
   - Proportionalitäten aus der Physik
