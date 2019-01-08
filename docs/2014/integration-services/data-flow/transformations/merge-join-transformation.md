---
title: Transformation für Zusammenführungsjoin | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointrans.f1
helpviewer_keywords:
- datasets [Integration Services]
- Merge Join transformation
- datasets [Integration Services], joining
- joining datasets [Integration Services]
- joins [SQL Server], SSIS
ms.assetid: cd8b0412-f83b-4bd2-b227-e53dcfd941a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e1a581536bb4f2a07dbbdf3d6ca187ac4a6f5250
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767182"
---
# <a name="merge-join-transformation"></a>Merge Join Transformation
  Die Transformation für Zusammenführungjoins stellt eine Ausgabe bereit, die durch Verknüpfen von zwei sortierten Datasets mithilfe einer FULL JOIN-, LEFT JOIN- oder INNER JOIN-Anweisung generiert wird. Beispielsweise können Sie mit einer LEFT JOIN-Anweisung eine Tabelle, die Produktinformationen einschließt, mit einer Tabelle verknüpfen, die das Land bzw. die Region auflistet, in der ein Produkt hergestellt wurde. Das Ergebnis ist eine Tabelle, in der alle Produkte und deren Ursprungsland/-region aufgelistet sind.  
  
 Es gibt folgende Möglichkeiten, um die Transformation für Zusammenführungsjoin zu konfigurieren:  
  
-   Geben Sie die Verknüpfung mit einer FULL JOIN-, LEFT JOIN- oder INNER JOIN-Anweisung an.  
  
-   Geben Sie die vom Join verwendeten Spalten an.  
  
-   Geben Sie an, ob die Transformation NULL-Werte als identisch mit anderen NULL-Werten behandelt.  
  
    > [!NOTE]  
    >  Wenn NULL-Werte nicht als identische Werte behandelt werden, behandelt die Transformation NULL-Werte wie die SQL Server-Datenbank-Engine.  
  
 Diese Transformation weist zwei Eingaben und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="input-requirements"></a>Eingabeanforderungen  
 Die Transformation für Zusammenführungsjoin erfordert als Eingabe sortierte Daten. Weitere Informationen zu dieser wichtigen Anforderung finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
## <a name="join-requirements"></a>Joinanforderungen  
 Für die Transformation für Zusammenführungsjoin müssen die verknüpften Spalten übereinstimmende Metadaten aufweisen. Beispielsweise kann eine Spalte mit einem numerischen Datentyp nicht mit einer Spalte mit einem Zeichendatentyp verknüpft werden. Wenn die Daten einen Zeichenfolgen-Datentyp aufweisen, muss die Länge der Spalte in der zweiten Eingabe kleiner oder gleich der Länge der Spalte in der ersten Eingabe sein, mit der diese zusammengeführt wird.  
  
## <a name="buffer-throttling"></a>Pufferdrosselung  
 Der Wert der `MaxBuffersPerInput`-Eigenschaft muss nicht mehr konfiguriert werden, da Microsoft Änderungen vorgenommen hat, die das Risiko einer übermäßigen Arbeitsspeicherbelegung bei der Transformation für Zusammenführungsjoins reduzieren. Dieses Problem trat in einigen Fällen auf, wenn durch die Eingaben des Zusammenführungsjoins unregelmäßige Daten erzeugt wurden.  
  
## <a name="related-tasks"></a>Related Tasks  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften für diese Transformation anzuzeigen:  
  
-   [Erweitern eines Datasets mithilfe der Transformation für Zusammenführungsjoins](merge-join-transformation.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Transformations-Editor für Zusammenführungsjoin](../../merge-join-transformation-editor.md)   
 [Transformation für Zusammenführen](merge-transformation.md)   
 [Transformation für UNION ALL](union-all-transformation.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
