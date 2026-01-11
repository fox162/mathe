# Maxima Befehle für ODEs

## Notation / Schreibweise

| Mathematik    | Maxima           | Erklärung |
| ------------- | ---------------- | --------- |
| $y'$          | `'diff(y,x)`     | Ableitung von y nach x |
| $y^{(n)}$     | `'diff(y,x,n)`   | n-te Ableitung |
| C (Konstante) | `%c`, `%k1`, ... | Integrationskonstanten |
| $e$ (Euler)   | `%e`             | Eulersche Zahl |
| $\pi$         | `%pi`            | Kreiszahl Pi |
| $\infty$      | `inf`            | Unendlich |

---

## ODE-spezifische Befehle

### 1. ODE lösen (allgemein)
```maxima
ode2(gleichung, abhängige_var, unabhängige_var);
```

**Beispiel:**
```maxima
/* y' - 2y = 0 */
ode2('diff(y,x) - 2*y = 0, y, x);
/* Ausgabe: y = %c * %e^(2*x) */
```

### 2. ODE mit Anfangsbedingung lösen
```maxima
ic1(lösung, x=x0, y=y0);
```

**Beispiel:**
```maxima
/* Erst ODE lösen */
sol: ode2('diff(y,x) - 2*y = 0, y, x);
/* Mit Anfangsbedingung y(0) = 3 */
ic1(sol, x=0, y=3);
/* Ausgabe: y = 3 * %e^(2*x) */
```

### 3. ODE 2. Ordnung mit 2 Anfangsbedingungen
```maxima
ic2(lösung, x=x0, y=y0, 'diff(y,x)=y0_prime);
```

**Beispiel:**
```maxima
/* y'' + y = 0 */
sol: ode2('diff(y,x,2) + y = 0, y, x);
/* Mit y(0) = 1, y'(0) = 0 */
ic2(sol, x=0, y=1, 'diff(y,x)=0);
```

### 4. Numerische Lösung (bei komplexen ODEs)
```maxima
load("dynamics");
rk(gleichung, y, anfangswert, [t, start, ende, schrittweite]);
```

---

## Grundlegende Mathematik-Befehle

### Algebraische Umformungen
```maxima
/* Gleichung nach Variable auflösen */
solve(gleichung, variable);
/* Beispiel: */
solve(x^2 - 4 = 0, x);  /* [x = -2, x = 2] */

/* Vereinfachen */
ratsimp(ausdruck);      /* Rational vereinfachen */
expand(ausdruck);        /* Ausmultiplizieren */
factor(ausdruck);        /* Faktorisieren */

/* Beispiele: */
expand((x+1)^2);         /* x^2 + 2*x + 1 */
factor(x^2 - 4);         /* (x-2)*(x+2) */
```

### Substitution
```maxima
subst(neu, alt, ausdruck);
```

**Beispiele:**
```maxima
/* x durch 2 ersetzen */
subst(2, x, x^2 + 3*x);  /* 10 */

/* e^x durch u ersetzen */
subst(u, %e^x, %e^(2*x) + %e^x);  /* u^2 + u */
```

### Integration
```maxima
/* Unbestimmtes Integral */
integrate(funktion, variable);

/* Bestimmtes Integral */
integrate(funktion, variable, untere_grenze, obere_grenze);
```

**Beispiele:**
```maxima
integrate(x^2, x);           /* x^3/3 */
integrate(1/x, x);           /* log(x) */
integrate(x^2, x, 0, 1);     /* 1/3 */
integrate(%e^x, x);          /* %e^x */
integrate(sin(x), x);        /* -cos(x) */
```

### Ableitung
```maxima
/* Ableitung */
diff(funktion, variable);

/* n-te Ableitung */
diff(funktion, variable, n);
```

**Beispiele:**
```maxima
diff(x^3, x);           /* 3*x^2 */
diff(sin(x), x);        /* cos(x) */
diff(x^3, x, 2);        /* 6*x (zweite Ableitung) */
```

### Auswerten / Evaluieren
```maxima
/* Ausdruck an einer Stelle auswerten */
at(ausdruck, [variable = wert]);

/* oder mit subst: */
subst(wert, variable, ausdruck);
```

**Beispiele:**
```maxima
at(x^2 + 1, [x = 3]);    /* 10 */
subst(3, x, x^2 + 1);    /* 10 */
```

---

## Vollständige Beispiele

### Beispiel 1: Einfache ODE mit Anfangsbedingung
```maxima
/* y' = 2xy mit y(0) = 1 */

/* Schritt 1: ODE lösen */
sol: ode2('diff(y,x) = 2*x*y, y, x);
/* Ausgabe: y = %c * %e^(x^2) */

/* Schritt 2: Anfangsbedingung einsetzen */
partikulaer: ic1(sol, x=0, y=1);
/* Ausgabe: y = %e^(x^2) */

/* Schritt 3: An Stelle x=1 auswerten */
at(partikulaer, [x=1]);
/* Ausgabe: %e */
```

### Beispiel 2: Inhomogene ODE
```maxima
/* y' - 2y = 5*x^2 mit y(0) = 3 */

/* ODE lösen */
sol: ode2('diff(y,x) - 2*y = 5*x^2, y, x);

/* Mit Anfangsbedingung */
partikulaer: ic1(sol, x=0, y=3);

/* Ergebnis anzeigen */
partikulaer;
```

### Beispiel 3: Newtonsches Abkühlungsgesetz
```maxima
/* T' = -k*(T - 23) mit T(0) = 205 */

/* ODE aufstellen und lösen */
sol: ode2('diff(T,t) = -k*(T - 23), T, t);
/* Ausgabe: T = %c * %e^(-k*t) + 23 */

/* Anfangsbedingung T(0) = 205 */
partikulaer: ic1(sol, t=0, T=205);
/* Ausgabe: T = 182 * %e^(-k*t) + 23 */

/* Für k=0.1, Zeit t=10 auswerten */
at(partikulaer, [k=0.1, t=10]);
```

---

## Nützliche Tipps

1. **Apostroph vor diff:** `'diff(y,x)` verhindert sofortige Auswertung
2. **Ergebnis speichern:** `sol: ode2(...);` um Ergebnis weiterzuverwenden
3. **Vereinfachen:** `ratsimp(lösung);` macht Ergebnis übersichtlicher
4. **Float-Ausgabe:** `float(ausdruck);` für Dezimalzahlen
5. **Gleichung definieren:** `eq: y = x^2;` dann mit `eq` weiterarbeiten

### Häufige Fehler vermeiden
- ❌ `diff(y,x)` ohne Apostroph → wird sofort ausgewertet (meist 0)
- ✅ `'diff(y,x)` mit Apostroph → symbolische Ableitung
- ❌ `ic1(y = %c*e^x, ...)` → Lösung direkt eingeben
- ✅ `ic1(sol, ...)` → Variable mit Lösung verwenden