# Testbed Constraints Datenmodell 'DMAV'

## Aufruf Testbed

```
java -jar .\_Runner\interlis-testbed-runner-1.0.0\lib\interlis-testbed-runner-1.0.0.jar -v .\_Runner\ilivalidator-1.14.3\ilivalidator-1.14.3.jar .\test_data\
```

## Beschreibung der initialen Failcases

Die Failcases sind so aufgebaut, dass sie durch eine inkrementelle Änderung des offiziellen DMAV-Testdatensatzes je einen Validierungsfehler auslösen.
In allen Fällen wird ein benannter MANDATORY CONSTRAINT verletzt. Nachfolgend sind die Failcases im Detail beschrieben.

### **Failcase #1: DELETE**
Im Untermodell **DMAV_Grundstuecke_V1_0** wird der
```
MANDATORY CONSTRAINT CH042402:
 	(INTERLIS.objectCount(Liegenschaft)>0 AND INTERLIS.objectCount(SelbstaendigesDauerndesRecht)==0 AND INTERLIS.objectCount(Bergwerk)==0)
 	OR (INTERLIS.objectCount(Liegenschaft)==0 AND INTERLIS.objectCount(SelbstaendigesDauerndesRecht)>0 AND INTERLIS.objectCount(Bergwerk)==0)
  	OR (INTERLIS.objectCount(Liegenschaft)==0 AND INTERLIS.objectCount(SelbstaendigesDauerndesRecht)==0 AND INTERLIS.objectCount(Bergwerk)>0)
```
verletzt, in dem das Objekt 73b015bb-1be6-4230-a00d-41b8f303bd80 der Klasse _SelbstaendigesDauerndesRecht_  gelöscht wird, das von Grundstück 8904bd52-8da6-4eda-9c5c-29539529c960 referenziert wird. Somit ist die Bedingung nicht mehr erfüllt, dass jedes Objekt der Klasse _Grundstueck_ genau entweder einem Objekt der Klasse _Liegenschaft_, _SelbstaendigesDauerndesRecht_ ODER _Bergwerk_ zugeordnet sein muss.

### **Failcase #2: INSERT (kombiniert)**
Im Untermodell **DMAV_Bodenbedeckung_V1_0** wird der
```
MANDATORY CONSTRAINT CH080402: Objektstatus!=#real OR Bodenbedeckungsart!=#Gebaeude OR DEFINED(EGID)
```
verletzt, indem ein neues Objekt der Klasse _Bodenbedeckung_ mit TID "test1127-1b78-477b-89dc-34c9ae734b95" und Bodenbedeckungsart Gebaeude (inklusive Geometrie) eingeführt. Das Attribut EGID wird dabei leer gelassen.

Weil die Bodenbedeckung keine Lücken zulässt (AREA-Geometrie), muss an der Stelle des neuen Gebäudes ein zusätzliches Donut Hole im bestehenden Bodenbedeckungs-Polygon (Bodenbedeckungsart Gartenanlage, TID "3ade9ad2-84d4-4da9-8553-d8031c7cd12b") eingefügt werden, dessen Geometrie mit dem neuen Gebäude identisch ist. Somit findet neben dem INSERT auch ein UPDATE-Prozess in diesem Inkrement statt.

### **Failcase #3: UPDATE**
Im Untermodell **DMAV_Grundstuecke_V1_0** wird der 
```
MANDATORY CONSTRAINT CH041201: NOT(DEFINED(Streitig)) OR DMAVTYM_Topologie_V1_0.covers(THIS,>>Geometrie,THIS,>>Streitig)
```
verletzt, indem die Geometrie eines Objekts der Klasse _Liegenschaft_, indem die Sekundärgeometrie (Attribut _Streitig_) an der X-Koordinate des ersten Stützpunktes um 3 Meter verschoben wird, sodass die Sekundärgeometrie keine Teilmenge der Primärgeometrie desselben Objekts mehr ist (Die strittige Grenze entspricht nicht mehr der Grundstücksgrenze).