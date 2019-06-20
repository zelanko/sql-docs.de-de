---
title: Parameter für | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b366ddd7a665112e6b40b814b13037a517d623a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149365"
---
# <a name="statement-parameters"></a>Anweisungsparameter
Ein *Parameter* ist eine Variable in einer SQL-Anweisung. Nehmen wir beispielsweise an, dass eine Parts-Tabelle die Spalten PartID, Beschreibung und Preis verfügt. Ein Teil ohne Parameter hinzufügen müssten Erstellen einer SQL­Anweisung, wie z. B.:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Obwohl diese Anweisung eine neue Bestellung einfügt, ist es keine gute Lösung für eine Anwendung, da die einzufügenden Werte in der Anwendung hartcodiert werden können. Alternativ kann zum Erstellen der SQL-Anweisung zur Laufzeit unter Verwendung der Werte eingefügt werden soll. Dies ist auch keine gute Lösung, wegen der Komplexität der erstellen-Anweisungen zur Laufzeit. Die beste Lösung ist, ersetzt die Elemente der **Werte** -Klausel mit dem Fragezeichen (?), oder *parametermarkierungen*:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Die Parametermarkierungen werden dann an Anwendungsvariablen gebunden. Um eine neue Zeile hinzuzufügen, muss die Anwendung nur die Werte der Variablen festlegen, und führen Sie die Anweisung. Der Treiber ruft dann die aktuellen Werte der Variablen ab und sendet sie an die Datenquelle. Wenn die Anweisung mehrmals ausgeführt wird, kann die Anwendung den Prozess sogar noch effizienter, indem Vorbereitung der Anweisung.  
  
 Die Anweisung, die oben gezeigte möglicherweise hart kodierte in auftragserfassungsanwendung um eine neue Zeile einzufügen. Parametermarkierungen sind jedoch nicht auf einer vertikale Anwendungen beschränkt. Für jede Anwendung vereinfachen sie die Schwierigkeit der SQL-Anweisungen zur Laufzeit durch das Vermeiden von Konvertierungen in und aus Text zu erstellen. Beispielsweise ist der soeben gezeigte Teil-ID am wahrscheinlichsten in der Anwendung als eine ganze Zahl gespeichert. Wenn die SQL-Anweisung ohne parametermarkierungen erstellt wird, die Anwendung muss die Teil-ID in Text konvertieren und die Datenquelle muss die Umstellung zurück auf eine ganze Zahl. Mithilfe einer parametermarkierung, kann die Anwendung die Teil-ID an den Treiber als ganze Zahl, senden die in der Regel es an die Datenquelle als eine ganze Zahl senden können. Dies spart zwei Konvertierungen. Lange Datenwerte ist dies sehr wichtig, weil die Textformen solche Werte häufig die zulässige Länge von einer SQL-Anweisung überschreiten.  
  
 Parameter sind nur an bestimmten Stellen in SQL-Anweisungen gültig. Sie sind z. B. in der select-Liste nicht zulässig (die Liste der Spalten von zurückgegeben werden eine **wählen** Anweisung), noch dürfen als beide Operanden des binären Operators wie z. B. das Gleichheitszeichen (=), da es unmöglich wäre Bestimmen Sie den Parametertyp an. Im Allgemeinen sind die Parameter gültig ist nur in-Anweisungen (Data Manipulation Language, DML), und nicht im-Anweisungen (Data Definition Language, Datendefinitionssprache). Weitere Informationen finden Sie unter [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md) in Anhang C: SQL-Grammatik.  
  
 Wenn die SQL-Anweisung für eine Prozedur, die benannte Parameter aufruft, kann verwendet werden. Benannte Parameter werden durch ihren Namen, nicht anhand ihrer Position in der SQL-Anweisung identifiziert. Diese gebunden werden können, durch einen Aufruf von **SQLBindParameter**, aber der Parameter wird durch die SQL_DESC_NAME-Felds, der die Implementierungsparameterdeskriptors (IPD), identifiziert, nicht von der *ParameterNumber* Argument **SQLBindParameter**. Sie können auch durch Aufrufen von gebunden **SQLSetDescField** oder **SQLSetDescRec**. Weitere Informationen zu benannten Parametern finden Sie unter [Bindungsparameter von Namen (Parameter genannt)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)weiter unten in diesem Abschnitt. Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Binden von Parametern](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Festlegen von Parameterwerten](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Abrufen von Ausgabeparametern von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Prozedurparameter](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Arrays für Parameterwerte](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)
