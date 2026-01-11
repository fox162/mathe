## Beispiel 1: Einfach
**ODE:** $y' = 2xy$

**Schritt 1-2:** Schreibe um: $\frac{dy}{dx} = 2xy$

**Schritt 3:** Trenne Variablen:

$$\frac{dy}{y} = 2x \, dx$$

**Schritt 4:** Integriere beide Seiten:

$$\int \frac{dy}{y} = \int 2x \, dx$$

$$\ln|y| = x^2 + C$$

**Schritt 5:** Löse nach $y$ auf:

$$|y| = e^{x^2 + C} = e^C \cdot e^{x^2}$$

$$y = A \cdot e^{x^2} \quad \text{(wobei $A = \pm e^C$)}$$

**Allgemeine Lösung:** $\boxed{y = A e^{x^2}}$

```maxima
(%i1)	kill(all);
(%o0)	done

(%i2)	gl1: 'diff(y,x, 1) =  2*x*y;
(gl1)	'diff(y,x,1)=2*x*y
/* dy/dx=2*x*y */

(%i3)	ode2(gl1, y, x);
(%o3)	y=%e^x^2*%c
/* y=A*e^(x^2) */

/* überprüfung der getrennten schreibweise */
/* 1/y=2x */
(%i4)	i1: integrate(1/y, y) = integrate(2*x, x);
(i1)	log(y)=x^2

(%i5)	solve(i1, y);
(%o5)	[y=%e^x^2]
/* selbes ergebnis --> */
```

## Beispiel 2: Mit Anfangsbedingung
**ODE mit AB:** $y' = -2xy$ mit $y(0) = 3$

**Schritt 1-4:** (wie oben, aber mit Minus)

$$\int \frac{dy}{y} = \int -2x \, dx$$

$$\ln|y| = -x^2 + C$$

$$y = A e^{-x^2}$$

**Schritt 5b - Anfangsbedingung einsetzen:**

$$y(0) = 3: \quad 3 = A e^0 = A$$

$$A = 3$$

**Partikuläre Lösung:** $\boxed{y = 3e^{-x^2}}$
```maxima
(%i1)	kill(all);
(%o0)	done

(%i1)	gl2: 'diff(y,x, 1) =  -2*x*y;
(gl2)	'diff(y,x,1)=-(2*x*y)
/* (d/dx)*y= -2*x*y */

(%i2)	loes: ode2(gl2, y, x);
(loes)	y=%e^(-x^2)*%c


(%i3)	y0: subst([x=0, y=3], loes);
(y0)	3=%c

/* in dem fall ist schon nach c aufgelöst */
(%i4)	solve(y0, %c);
(%o4)	[%c=3]

/* einsetzen in die allgemeine lösung */
(%i5)	subst(%c=3, loes);
(%o5)	y=3*%e^(-x^2)

/* partikuläre lösung (ic2 macht schritte automatisch)*/
(%i6)	ic1(loes, x=0, y=3);
(%o6)	y=3*%e^(-x^2)
```

## Beispiel 3: Etwas schwieriger
**ODE:** $y' = \frac{x}{y}$

**Schritt 1-3:** Trenne Variablen:

$$y \, dy = x \, dx$$

**Schritt 4:** Integriere:

$$\int y \, dy = \int x \, dx$$

$$\frac{y^2}{2} = \frac{x^2}{2} + C$$

$$y^2 = x^2 + K \quad \text{(wobei $K = 2C$)}$$

**Schritt 5:** Löse nach $y$ auf:
$$\boxed{y = \pm\sqrt{x^2 + K}}$$

```maxima
(%i1)	kill(all);
(%o0)	done

(%i1)	gl3: 'diff(y, x)=x/y;
(gl3)	'diff(y,x,1)=x/y
/* (d/dx)*y=x/y */

(%i2)	loes:  ode2(gl3,  y, x);
(loes)	y^2/2=x^2/2+%c

(%i3)	solve(loes, y);
(%o3)	[y=-sqrt(x^2+2*%c),y=sqrt(x^2+2*%c)]
/* y=±sqrt(x^2+K) mit K=2*C */
```
