# AC Dimmer Modul

1 Kanal, 3.3V/5V Logik, AC 50/60hz, 110V~400V
Der AC-Dimmer ist für die Steuerung der Wechselspannung ausgelegt, die einen Strom von bis zu 8A übertragen kann.

---

Der AC-Dimmer dient zur Steuerung der Wechselspannung, die bis zu **600V** und **16/24A** Strom übertragen kann. In den meisten Fällen wird der Dimmer zum Ein- und Ausschalten von Lampen oder Heizelementen verwendet, er kann aber auch in Lüftern, Pumpen, Luftreinigern usw. eingesetzt werden.

In letzter Zeit ist der Dimmer zu einer häufig genutzten Lösung für intelligente Heimsysteme geworden, z. B. wenn die Stromspannung sanft geändert werden muss. Der Strom schaltet sich langsam ein oder aus.

Der Leistungsteil des Dimmers ist vom Steuerteil isoliert, um die Möglichkeit einer Hochstromstörung des Mikrocontrollers auszuschließen.  

Der logische Pegel ist tolerant gegenüber **5V** und **3,3V**, daher kann er an Mikrocontroller mit 5V- oder 3,3V-Logikpegel angeschlossen werden.

In Arduino wird der Dimmer mit der Bibliothek `RBDdimmer.h` gesteuert, die externe Interrupts und Prozesszeit-Interrupts verwendet. Das vereinfacht das Schreiben des Codes und gibt mehr Verarbeitungszeit für den Hauptcode. Dadurch können mehrere Dimmer von einem Mikrocontroller aus gesteuert werden.

Die Bibliothek `RBDDimmer.h` und Beispiele finden Sie unter „Dokumente“ oder direkt auf GitHub: [RBDDimmer](https://github.com/RobotDynOfficial/RBDDimmer). Die Bibliothek wird regelmäßig aktualisiert, daher empfiehlt es sich, auf Updates zu prüfen oder den Newsletter zu abonnieren.

---

## Anschluss

Der Dimmer wird über zwei digitale Pins mit dem Arduino verbunden:

1. **Zero** – steuert den Übergang der Nullphase des Wechselstroms, zur Auslösung des Interrupt-Signals.  
2. **DIM/PSM** – zur Steuerung des Stroms.

Beachten Sie, dass **Zero** an bestimmte Interrupt-fähige Pins des Mikrocontrollers angeschlossen werden muss (je nach Modell: Uno, Nano, Leonardo, Mega).

---

## Theorie – Pulse Skip Modulation

Dimmen lässt sich durch **Pulse Skip Modulation** erreichen:

1. Ein oder mehrere Zyklen einer Sinuswelle werden an die Last übertragen, während die folgenden Zyklen blockiert werden.  
2. Teilweise Übertragung jeder Sinuswelle an die Last.  
3. Erzeugung modulierten Vollsinussignals mit variabler Frequenz (bis einige hundert Hz). Diese Methode erfordert spezielle leistungsstarke Wechselstromgeneratoren.  

Die Methoden 1 und 2 lassen sich am einfachsten mit einem Dimmer und passendem Programmcode realisieren. Dazu wird eine Schaltung benötigt, die den **Nulldurchgang** erkennt und einen **TRIAC** steuern kann.

---

## Spezifikation

| Parameter                  | Wert                                |
|-----------------------------|------------------------------------|
| Leistung                    | bis zu 600V                        |
| TRIAC                       | BTA16-600V / BTA24-600V           |
| Isolierung                  | Optokoppler                        |
| Logischer Pegel             | 3,3V / 5V                          |
| Nullpunkt                   | Logischer Pegel                     |
| Modulation (DIM/PWM)        | Logikpegel EIN/AUS TRIAC           |
| Signalstrom                 | >10mA                              |
| Umwelt                      | Für Innen- und Außeneinsatz        |
| Betriebstemperatur          | -20°C bis 80°C                     |
| Betriebsfeuchtigkeit        | Nur in trockener Umgebung           |
| ROHS3                       | Konform                             |

---

## Bibliothek und Skizzenbeispiele

- **Dimmer-Bibliothek:** [`RBDdimmer.h`](https://github.com/RobotDynOfficial/RBDDimmer)  
- Beispiele für Arduino-Sketches befinden sich im `examples/`-Ordner der Bibliothek.
