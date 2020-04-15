---
title: Anweisungsparameter | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306821"
---
# <a name="statement-parameters"></a>Anweisungsparameter
Ein *Parameter* ist eine Variable in einer SQL-Anweisung. Angenommen, eine Parts-Tabelle enthält Spalten mit dem Namen PartID, Beschreibung und Preis. Um ein Teil ohne Parameter hinzuzufügen, müssen Sie eine SQL-Anweisung erstellen, z. B.:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Obwohl diese Anweisung eine neue Order einfügt, ist sie keine gute Lösung für eine Auftragserfassungsanwendung, da die einzufügenden Werte in der Anwendung nicht hartcodiert werden können. Eine Alternative besteht darin, die SQL-Anweisung zur Laufzeit unter Verwendung der einzufügenden Werte zu erstellen. Dies ist auch keine gute Lösung, da Anweisungen zur Laufzeit komplex sind. Die beste Lösung besteht darin, die Elemente der **VALUES-Klausel** durch Fragezeichen (?) oder *Parametermarkierungen*zu ersetzen:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Die Parametermarkierungen werden dann an Anwendungsvariablen gebunden. Um eine neue Zeile hinzuzufügen, muss die Anwendung nur die Werte der Variablen festlegen und die Anweisung ausführen. Der Treiber ruft dann die aktuellen Werte der Variablen ab und sendet sie an die Datenquelle. Wenn die Anweisung mehrmals ausgeführt wird, kann die Anwendung den Prozess durch vorbereitende Anweisung noch effizienter gestalten.  
  
 Die soeben angezeigte Anweisung ist möglicherweise in einer Auftragseingabeanwendung hartcodiert, um eine neue Zeile einzufügen. Parametermarkierungen sind jedoch nicht auf vertikale Anwendungen beschränkt. Für jede Anwendung erleichtern sie das Erstellen von SQL-Anweisungen zur Laufzeit, indem Konvertierungen in und aus Text vermieden werden. Beispielsweise wird die soeben angezeigte Teile-ID höchstwahrscheinlich in der Anwendung als ganzzahlige Datei gespeichert. Wenn die SQL-Anweisung ohne Parametermarkierungen erstellt wird, muss die Anwendung die Teile-ID in Text konvertieren, und die Datenquelle muss sie wieder in eine ganze Zahl konvertieren. Mithilfe einer Parametermarkierung kann die Anwendung die Teile-ID als ganze Zahl an den Treiber senden, die sie in der Regel als ganze Zahl an die Datenquelle senden kann. Dadurch werden zwei Konvertierungen spart. Bei langen Datenwerten ist dies sehr wichtig, da die Textformen solcher Werte häufig die zulässige Länge einer SQL-Anweisung überschreiten.  
  
 Parameter sind nur an bestimmten Stellen in SQL-Anweisungen gültig. Sie sind z. B. in der Auswahlliste (die Liste der Spalten, die von einer **SELECT-Anweisung** zurückgegeben werden sollen) nicht zulässig, noch als beide Operanden eines binären Operators wie dem Gleichheitszeichen (=), da es unmöglich wäre, den Parametertyp zu bestimmen. Im Allgemeinen sind Parameter nur in DML-Anweisungen (Data Manipulation Language) und nicht in DDL-Anweisungen (Data Definition Language) gültig. Weitere Informationen finden Sie unter [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md) in Anhang C: SQL Grammar.  
  
 Wenn die SQL-Anweisung eine Prozedur aufruft, können benannte Parameter verwendet werden. Benannte Parameter werden durch ihre Namen identifiziert, nicht durch ihre Position in der SQL-Anweisung. Sie können durch einen Aufruf von **SQLBindParameter**gebunden werden, aber der Parameter wird durch das SQL_DESC_NAME Feld der IPD (Implementierungsparameterdeskriptor) und nicht durch das *ParameterNumber-Argument* von **SQLBindParameter**identifiziert. Sie können auch durch Aufrufen von **SQLSetDescField** oder **SQLSetDescRec**gebunden werden. Weitere Informationen zu benannten Parametern finden Sie weiter unten in diesem Abschnitt unter [Bindungsparameter nach Name (Benannte Parameter).](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md) Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parametern](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Festlegen von Parameterwerten](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Abrufen von Ausgabeparametern durch SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Prozedurparameter](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Arrays für Parameterwerte](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)
