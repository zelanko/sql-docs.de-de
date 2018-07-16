---
title: Aufrufen von gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb799a4e366c0301998b46d7244438aabd2c4411
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299150"
---
# <a name="calling-stored-procedures"></a>Aufrufen von gespeicherten Prozeduren
  Gespeicherte Prozeduren können auf dem Server oder aus einer Clientanwendung aufgerufen werden. In beiden Fällen werden gespeicherte Prozeduren immer auf dem Server ausgeführt, entweder im Kontext des Servers oder einer Datenbank. Zum Ausführen einer gespeicherten Prozedur sind keine besonderen Berechtigungen erforderlich. Nach dem Hinzufügen einer gespeicherten Prozedur von einer Assembly zum Server- oder Datenbankkontext kann diese gespeicherte Prozedur von jedem Benutzer ausgeführt werden, sofern die Rolle des Benutzers die von der gespeicherten Prozedur durchgeführten Aktionen ermöglicht.  
  
 Eine gespeicherte Prozedur wird in MDX auf dieselbe Weise wie eine systeminterne MDX-Funktion aufgerufen. Für eine gespeicherte Prozedur ohne Parameter wird der Name der Prozedur und ein leeres Paar Klammern verwendet, wie im Folgenden gezeigt:  
  
```  
MyStoredProcedure()  
```  
  
 Falls die gespeicherte Prozedur Parameter hat, werden diese in der richtigen Reihenfolge, durch Kommas getrennt, angegeben. Das folgende Beispiel zeigt eine gespeicherte Beispielprozedur mit drei Parametern:  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a>Aufrufen von gespeicherten Prozeduren in MDX-Abfragen  
 In allen MDX-Abfragen muss die gespeicherte Prozedur den für einen MDX-Ausdruck erforderlichen, syntaktisch richtigen Typ zurückgeben. Wenn die gespeicherte Prozedur nicht den richtigen Typ zurückgibt, tritt ein MDX-Fehler auf. Die folgenden Beispiele zeigen gespeicherte Prozeduren, die eine Menge, ein Element und das Ergebnis einer mathematischen Operation zurückgeben.  
  
### <a name="returning-a-set"></a>Zurückgeben einer Menge  
 In den folgenden Beispielen wird die gespeicherte Prozedur MySproc implementiert, die eine Menge zurückgibt. Im ersten Beispiel gibt MySproc die Menge direkt an den SELECT-Ausdruck zurück. In den nächsten beiden Beispielen gibt MySproc die Menge als Argument für die Funktionen Crossjoin und DrilldownLevel zurück.  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a>Zurückgeben eines Elements  
 Das folgende Beispiel zeigt die Funktion MySproc, die ein Element zurückgibt:  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a>Zurückgeben des Ergebnisses einer mathematischen Operation  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a>Aufrufen von gespeicherten Prozeduren mit der CALL-Anweisung  
 Gespeicherte Prozeduren können mithilfe der MDX-Anweisung `Call` außerhalb des Kontexts einer MDX-Abfrage aufgerufen werden.  
  
 Sie können diese Methode verwenden, um entweder die Nebeneffekte einer gespeicherten Abfrage zu instanziieren, oder damit die Anwendung die Ergebnisse einer gespeicherten Abfrage erhält. Die `Call`-Anweisung wird häufig verwendet, um mithilfe von Analysis Management Objects (AMO) administrative Funktionen auszuführen, die kein Ergebnis zurückzugeben brauchen. Der folgende Befehl ruft beispielsweise eine gespeicherte Prozedur auf:  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 Rowset ist der einzige unterstützte Typ, der von einer gespeicherten Prozedur in einer `Call`-Anweisung zurückgegeben wird. Die Serialisierung für ein Rowset wird durch XML for Analysis definiert. Wenn eine gespeicherte Prozedur in einer `Call`-Anweisung einen anderen Typ zurückgibt, wird dieser ignoriert und nicht in XML an die aufrufende Anwendung zurückgegeben. Weitere Informationen zu XMLA-Rowsets (XML for Analysis) finden Sie unter XMLA-Schemarowsets.  
  
 Wenn eine gespeicherte Prozedur ein .NET-Rowset zurückgibt, konvertiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] das Ergebnis auf dem Server in ein XMLA-Rowset. Das XMLA-Rowset wird immer von einer gespeicherten Prozedur in der `Call`-Funktion zurückgegeben. Wenn ein Dataset Funktionen enthält, die nicht in einem XMLA-Rowset ausgedrückt werden können, tritt ein Fehler auf.  
  
 Prozeduren, die void zurückgeben (wie z. B. Unterroutinen in Visual Basic), können ebenfalls mit dem CALL-Schlüsselwort verwendet werden. Beispielsweise wird die MyVoidFunction()-Funktion in einer MDX-Anweisung mit folgender Syntax verwendet:  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren gespeicherter Prozeduren](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
