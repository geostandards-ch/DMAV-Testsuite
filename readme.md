# Testbed Constraints Datenmodell 'DMAV'

## Constraintmodelle
Die nich im Hauptmodelle enthaltenen Constraints wurden in zusätzlichen Validierungsmodellen pro Modell formuliert. Folgende zusätzliche Validierungsmodelle bestehen:
* DMAV_V1_0_Bodenbedeckung_Validierung
* DMAV_V1_0_Einzelobjekte_Validierung
* DMAV_V1_0_FixpunkteKategorie3_Validierung
* DMAV_V1_0_Gebaeudeadressen_Validierung
* DMAV_V1_0_Grundstuecke_Validierung
* DMAV_V1_0_HoheitsgrenzenAV_Validierung
* DMAV_V1_0_Nomenklatur_Validierung
* DMAV_V1_0_Rohrleitungen_Validierung
* DMAV_V1_0_Toleranzstufen_Validierung

## Aufruf Testbed

DMAV_Bodenbedeckung_V1_0
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Bodenbedeckung_Validierung.ini ./Testsuite_DMAV/DMAV_Bodenbedeckung_V1_0
```

DMAV_DauerndeBodenverschiebungen_V1_0
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar ./Testsuite_DMAV/DMAV_DauerndeBodenverschiebungen_V1_0
```

DMAV_Dienstbarkeitsgrenzen_V1_0
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar ./Testsuite_DMAV/DMAV_Dienstbarkeitsgrenzen_V1_0
```

DMAV_Einzelobjekte_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Einzelobjekte_Validierung.ini ./Testsuite_DMAV/DMAV_Einzelobjekte_V1_0
```

DMAV_FixpunkteAVKategorie3_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_FixpunkteKategorie3_Validierung.ini ./Testsuite_DMAV/DMAV_FixpunkteAVKategorie3_V1_0
```

DMAV_Gebaeudeadressen_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Gebaeudeadressen_Validierung.ini ./Testsuite_DMAV/DMAV_Gebaeudeadressen_V1_0
```

DMAV_HoheitsgrenzenAV_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_HoheitsgrenzenAV_Validierung.ini ./Testsuite_DMAV/DMAV_HoheitsgrenzenAV_V1_0
```

DMAV_Grundstuecke_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Grundstuecke_Validierung.ini ./Testsuite_DMAV/DMAV_Grundstuecke_V1_0
```

DMAV_Nomenklatur_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Nomenklatur_Validierung.ini ./Testsuite_DMAV/DMAV_Nomenklatur_V1_0
```

DMAV_Toleranzstufen_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Toleranzstufen_Validierung.ini ./Testsuite_DMAV/DMAV_Toleranzstufen_V1_0
```

DMAV_Rohrleitungen_V1_0:
```
java -jar ./_Runner/interlis-testbed-runner-1.0.1/lib/interlis-testbed-runner-1.0.1-SNAPSHOT.jar -v ./_Runner/ilivalidator-1.15.0/ilivalidator-1.15.0-SNAPSHOT.jar --config ./Testsuite_DMAV/DMAV_V1_0_Rohrleitungen_Validierung.ini ./Testsuite_DMAV/DMAV_Rohrleitungen_V1_0
```

## Beschreibung der initialen Failcases

Die Failcases sind so aufgebaut, dass sie durch eine inkrementelle Änderung des offiziellen DMAV-Testdatensatzes je einen Validierungsfehler auslösen. Bei der Testausführung wird der vollständige Datensatz um dieses fehlerhalfte Inkrement erweitert. Für die Zusammenführung der beiden Transferdateien stehen folgende drei Operationen zur Verfügung: 
* INSERT: ein neuer Datensatz wird der Transferdatei hinzugefügt
* UPDATE: ein bestehender Datensatz wird aktualisiert ( :information_source: Element muss vollständig definiert werden und nicht nur die geänderten Attribute)
* DELETE: ein Datensatz wird aus dem Transfer entfernt

## Hinweis zu Drittdaten und Referenzmodellen
Im Repository sind alle verwendeten Referenzmodelle abgelegt. Beim Aufruf der Testsuite werden die Modelle aus dem Repository verwendet, welche zum jeweiligen Zeitpunkt aktuell waren und zu den Failcases passen.
Externe Daten (Liste aller Gemeinden, Dienstdaten) wurden in die Transferdateien integriert. So wird sichergestellt, dass die Failcases nicht durch die Veränderung von externen Daten zu neuen / anderen Fehlern führen.
