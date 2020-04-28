---
title: Anweisungs Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement parameters [ODBC]
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02327ff4bb6a1ac3ac57fbf7d3c6b09b70c11534
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306821"
---
# <a name="statement-parameters"></a>Anweisungsparameter
Bei einem *Parameter* handelt es sich um eine Variable in einer SQL-Anweisung. Nehmen wir beispielsweise an, dass eine parts-Tabelle Spaltennamens partid, Description und Price enthält. Zum Hinzufügen eines Teils ohne Parameter müssen Sie eine SQL-Anweisung wie die folgende erstellen:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Obwohl mit dieser Anweisung eine neue Bestellung eingefügt wird, ist Sie keine gute Lösung für eine Auftragseingangs Anwendung, da die einzufügenden Werte in der Anwendung nicht hart codiert werden können. Eine Alternative besteht darin, die SQL-Anweisung zur Laufzeit zu erstellen, indem die einzufügenden Werte verwendet werden. Dies ist auch keine gute Lösung, aufgrund der Komplexität der konstruierten Anweisungen zur Laufzeit. Die beste Lösung besteht darin, die Elemente der **Values** -Klausel durch Fragezeichen (?) oder *Parameter Markierungen*zu ersetzen:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Die Parametermarkierungen werden dann an Anwendungsvariablen gebunden. Um eine neue Zeile hinzuzufügen, kann die Anwendung nur die Werte der Variablen festlegen und die Anweisung ausführen. Der Treiber ruft dann die aktuellen Werte der Variablen ab und sendet sie an die Datenquelle. Wenn die Anweisung mehrmals ausgeführt wird, kann die Anwendung den Prozess durch Vorbereiten der Anweisung noch effizienter gestalten.  
  
 Die soeben angezeigte Anweisung kann in einer Anwendung für die Bestell Eingabe hart codiert sein, um eine neue Zeile einzufügen. Parameter Markierungen sind jedoch nicht auf vertikale Anwendungen beschränkt. Für jede Anwendung vereinfachen Sie die Schwierigkeit, SQL-Anweisungen zur Laufzeit zu erstellen, indem Sie Konvertierungen in und aus Text vermeiden. Beispielsweise ist die soeben angezeigte Teile-ID höchstwahrscheinlich in der Anwendung als ganze Zahl gespeichert. Wenn die SQL-Anweisung ohne Parametermarker erstellt wird, muss die Teil-ID von der Anwendung in Text konvertiert werden, und die Datenquelle muss Sie zurück in eine ganze Zahl konvertieren. Wenn Sie einen Parametermarker verwenden, kann die Anwendung die Teile-ID als Ganzzahl an den Treiber senden, die Sie in der Regel als Ganzzahl an die Datenquelle senden kann. Dadurch werden zwei Konvertierungen eingespart. Bei langen Datenwerten ist dies sehr wichtig, da die Textformen dieser Werte häufig die zulässige Länge einer SQL-Anweisung überschreiten.  
  
 Parameter sind nur an bestimmten Stellen in SQL-Anweisungen gültig. Beispielsweise sind Sie in der SELECT-Liste nicht zulässig (die Liste der Spalten, die von einer **Select** -Anweisung zurückgegeben werden sollen), und Sie sind nicht als beide Operanden eines binären Operators (z. b. Gleichheitszeichen (=)) zulässig, da der Parametertyp nicht bestimmt werden kann. Im Allgemeinen sind Parameter nur in DML-Anweisungen (Data Manipulation Language, Daten Bearbeitungs Sprache) und nicht in DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) gültig. Weitere Informationen finden Sie unter [Parameter Markierungen](../../../odbc/reference/appendixes/parameter-markers.md) in Anhang C: SQL-Grammatik.  
  
 Wenn die SQL-Anweisung eine Prozedur aufruft, können benannte Parameter verwendet werden. Benannte Parameter werden anhand ihrer Namen identifiziert, nicht anhand ihrer Position in der SQL-Anweisung. Sie können durch einen **SQLBindParameter**-Befehl gebunden werden, aber der Parameter wird durch das SQL_DESC_NAME-Feld der IPD (Implementierungs Parameter Deskriptor) identifiziert, nicht durch das *Parameter Number* -Argument von **SQLBindParameter**. Sie können auch durch Aufrufen von **SQLSetDescField** oder **SQLSetDescRec**gebunden werden. Weitere Informationen zu benannten Parametern finden Sie unter [Binden von Parametern anhand des Namens (benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)weiter unten in diesem Abschnitt. Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parametern](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Festlegen von Parameterwerten](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Abrufen von Ausgabeparametern durch SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Prozedurparameter](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Arrays für Parameterwerte](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)
