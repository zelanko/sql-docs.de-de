---
title: Transformieren von Daten mit Transformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9fb4014688f1899e813d1df3e677caf9ad7bfbf1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770301"
---
# <a name="transform-data-with-transformations"></a>Transformieren von Daten mit Transformationen
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] schließt drei verschiedene Arten von Datenflusskomponenten ein: Quellen, Transformationen und Ziele.  
  
 Im folgenden Diagramm wird ein einfacher Datenfluss mit einer Quelle, zwei Transformationen und einem Ziel dargestellt.  
  
 ![Data flow](../../media/mw-dts-08.gif "Data flow")  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Transformationen stellen die folgende Funktionalität bereit:  
  
-   Teilen, Kopieren und Zusammenführen von Rowsets und Ausführen von Suchvorgängen.  
  
-   Aktualisieren von Spaltenwerten und Erstellen neuer Spalten durch Anwenden von Transformationen, wie z. B. das Ändern von Großbuchstaben in Kleinbuchstaben.  
  
-   Ausführen von Business Intelligence-Vorgängen, wie z. B. das Bereinigen von Daten, Text Mining oder das Ausführen von Data Mining-Vorhersageabfragen.  
  
-   Erstellen neuer Rowsets, die aus Aggregatwerten oder sortierten Werten, Stichprobendaten oder pivotierten bzw. entpivotierten Daten bestehen.  
  
-   Ausführen von Aufgaben, wie z. B. das Exportieren und Importieren von Daten, das Bereitstellen von Überwachungsinformationen sowie das Verwenden von langsam veränderlichen Dimensionen.  
  
 Weitere Informationen finden Sie unter [Integration Services Transformations](integration-services-transformations.md).  
  
 Sie können auch benutzerdefinierte Transformationen erstellen. Weitere Informationen finden Sie unter [Entwickeln einer benutzerdefinierten Datenflusskomponente](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) und [Entwickeln bestimmter Arten von Datenflusskomponenten](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).  
  
 Nachdem Sie dem Datenfluss-Designer die Transformation hinzugefügt haben, jedoch bevor Sie die Transformation konfigurieren, verbinden Sie die Transformation mit dem Datenfluss. Hierzu verbinden Sie die Ausgabe einer anderen Transformation oder Quelle im Datenfluss mit der Eingabe dieser Transformation. Der Konnektor zwischen den beiden Datenflusskomponenten wird als Pfad bezeichnet. Weitere Informationen zum Verbinden von Komponenten und zum Verwenden von Pfaden finden Sie unter [Verbinden von Komponenten mit Pfaden](../../connect-components-with-paths.md).  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a>So fügen Sie einem Datenfluss eine Transformation hinzu  
  
-   [Hinzufügen oder Löschen einer Komponente im Datenfluss](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a>So verbinden Sie eine Transformation mit einem Datenfluss  
  
-   [Verbinden von Komponenten in einem Datenfluss](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a>So legen Sie die Eigenschaften einer Transformation fest  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenflusstask](../../control-flow/data-flow-task.md)   
 [Datenfluss](../data-flow.md)   
 [Verbinden von Komponenten mit Pfaden](../../connect-components-with-paths.md)   
 [Fehlerbehandlung in Daten](../error-handling-in-data.md)   
 [Datenfluss](../data-flow.md)  
  
  
