---
title: Transformation für Zusammenführen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 741ea39f6a60d7c9f52fb901a1b038a352e948b5
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374208"
---
# <a name="merge-transformation"></a>Transformation für Zusammenführen
  Die Transformation für Zusammenführen fasst zwei sortierte Datasets zu einem Dataset zusammen. Die Zeilen aus jedem Dataset werden basierend auf Werten in den Schlüsselspalten in die Ausgabe eingefügt.  
  
 Durch Einschließen der Transformation für Zusammenführen in einen Datenfluss können Sie die folgenden Aufgaben ausführen:  
  
-   Zusammenführen von Daten aus zwei Datenquellen, wie z. B. Tabellen und Dateien.  
  
-   Erstellen komplexer Datasets durch Schachteln von Transformationen für Zusammenführen.  
  
-   Erneutes Zusammenführen von Zeilen nach dem Korrigieren von Fehlern in den Daten.  
  
 Die Transformation für Zusammenführen ist mit den Transformationen für UNION ALL vergleichbar. Verwenden Sie die Transformation für UNION ALL in folgenden Situationen anstelle der Transformation für Zusammenführen:  
  
-   Die Transformationseingaben werden nicht sortiert.  
  
-   Die kombinierte Ausgabe muss nicht sortiert werden.  
  
-   Die Transformation weist mehr als zwei Eingaben auf.  
  
## <a name="input-requirements"></a>Eingabeanforderungen  
 Die Transformation für Zusammenführen erfordert als Eingabe sortierte Daten. Weitere Informationen zu dieser wichtigen Anforderung finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Für die Transformation für Zusammenführung müssen die zusammengeführten Spalten außerdem in ihren Ausgaben übereinstimmende Metadaten aufweisen. Beispielsweise kann eine Spalte mit einem numerischen Datentyp nicht mit einer Spalte mit einem Zeichendatentyp zusammengeführt werden. Wenn die Daten einen Zeichenfolgen-Datentyp aufweisen, muss die Länge der Spalte in der zweiten Eingabe kleiner oder gleich der Länge der Spalte in der ersten Eingabe sein, mit der diese zusammengeführt wird.  
  
 Im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer ordnet die Benutzeroberfläche für die Transformation für Zusammenführung automatisch Spalten mit den gleichen Metadaten zu. Sie können dann manuell andere Spalten mit kompatiblen Datentypen zuordnen.  
  
 Diese Transformation weist zwei Eingaben und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-merge-transformation"></a>Konfiguration der Zusammenführungstransformation  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Zusammenführen** festlegen können, finden Sie unter [Merge Transformation Editor](../../merge-transformation-editor.md).  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu anzuzeigen, die Sie programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Nähere Informationen zum Festlegen von Eigenschaften finden Sie in den folgenden Themen:  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Transformation für Zusammenführungsjoin](merge-join-transformation.md)   
 [Transformation für UNION ALL](union-all-transformation.md)   
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
