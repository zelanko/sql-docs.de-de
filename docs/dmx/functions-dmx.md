---
title: Funktionen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 891bad9f62174ec00451e533fe94063a21dc62af
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971679"
---
# <a name="functions-dmx"></a>Funktionen (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Wenn Sie in Data Mining-Erweiterungen (DMX) verwenden, um Objekte in abzufragen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , können Sie Funktionen verwenden, um mehr Informationen als nur die Werte in den Spalten im Data Mining Modell oder Eingabe DataSet zurückzugeben. Beispielsweise können Sie DMX-Abfragen verwenden, um nicht nur den Vorhersagewert einer Spalte, sondern auch die Wahrscheinlichkeit zurückzugeben, dass die Vorhersage richtig ist. Zusätzlich zu den DMX-Funktionen können Sie Funktionen von Microsoft Visual Basic für Applikationen (VBA) und von Microsoft Excel sowie gespeicherte Prozeduren verwenden.  
  
## <a name="dmx-functions"></a>DMX-Funktionen  
 Mit DMX-Funktionen können Sie folgende Aufgaben ausführen:  
  
-   Zurückgeben von Vorhersagen.  
  
-   Zurückgeben von statistischen Informationen zu einer Vorhersage, so z. B. die Wahrscheinlichkeit und den Unterstützungswert.  
  
-   Filtern von Abfrageergebnissen.  
  
-   Umordnen eines Tabellenausdrucks.  
  
 Die meisten DMX-Funktionen geben einen Skalarwert (z. B. ist der Unterstützungswert einer Vorhersage ein Skalarwert), einige Funktionen geben aber ein tabellarisches Ergebnis zurück. Beispielsweise gibt die Funktion "präthistogram" eine Tabelle zurück, die die Unterstützung und Wahrscheinlichkeit für jeden Status der angegebenen vorhersagbaren Spalte enthält. Die Ergebnisse werden als neue tabellarische Spalte angezeigt.  
  
 **Weitere Informationen finden** Sie unter [allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md), [Data Mining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
## <a name="visual-basic-for-applications-vba-and-excel-functions"></a>VBA-Funktionen (Visual Basic für Applikationen) und Excel-Funktionen  
 Zusätzlich zu DMX-Funktionen können Sie aus DMX-Anweisungen eine Vielzahl von VBA- und Excel-Funktionen aufrufen. Beispielsweise können Sie die LCase-Funktion verwenden, um zu ändern, wie die ATTRIBUTE_NAME Spalte im TM_Decision_Tree Modell Inhalt angezeigt wird. Dies ist im folgenden Codebeispiel gezeigt.  
  
```  
SELECT lCase([Attribute_Name])   
FROM [TM_Decision_Tree].CONTENT  
```  
  
 Wenn die gleiche Funktion sowohl in VBA als auch in Excel vorhanden ist, müssen Sie den Funktionsnamen in der DMX-Anweisung mit **VBA** oder **Excel**als Präfix versehen. Beispielsweise würden Sie `VBA!Log` oder `Excel!Log` verwenden. Wenn es die VBA- oder Excel-Funktion, die Sie verwenden möchten, auch in DMX oder MDX (Mehrdimensional Expressions) gibt oder wenn der Funktionsname ein Dollarzeichen ($) enthält, müssen Sie den Namen in eckige Klammern ([]) setzen. Die Funktion wird dann beispielsweise mit `[VBA!Format]` aufgerufen.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 Mit den üblichen Programmiersprachen für Laufzeitprozeduren können Sie gespeicherte Prozeduren erstellen, die die Funktionalität von DMX erweitern. Beispielsweise gibt ein Regressions Struktur-Mining Modell Koeffizienten zurück, wie z. B. a, B usw., die die Regressionsgleichung beschreiben, aber das Modell gibt die Formel nicht zurück, wie z. B. a + BX = y. Für einen solchen Fall können Sie eine gespeicherte Prozedur schreiben, in der das Data Mining-Modellobjekt dazu verwendet wird, das Inhaltsschema auszuwerten und die Regressionsgleichung als Ausgabe zurückzugeben. Auf diese Weise kann eine DMX-Anweisung eine Liste der Regressionsgleichungen als Teil eines Abfrageergebnisses zurückgeben.  
  
 **Weitere Informationen: Verwaltung von mehr** [dimensionalen modellassemblys](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-assemblies-management)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
