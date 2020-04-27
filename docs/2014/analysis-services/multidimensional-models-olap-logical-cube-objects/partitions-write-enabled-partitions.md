---
title: Partitionen mit aktiviertem Schreibzugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], write-enabled
- partitions [Analysis Services], storage
- writeback [Analysis Services], partitions
- storing data [Analysis Services], partitions
ms.assetid: 46e7683f-03ce-4af2-bd99-a5203733d723
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13864dba5cac0274204050a8c78730de29f3321e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727174"
---
# <a name="write-enabled-partitions"></a>Partitionen mit aktiviertem Schreibzugriff
  Die Daten in einem Cube sind im Allgemeinen schreibgeschützt. In bestimmten Szenarien kann es jedoch erwünscht sein, den Schreibzugriff für eine Partition zu aktivieren. Partitionen mit aktiviertem Schreibzugriff werden verwendet, um Benutzern im geschäftlichen Bereich das Untersuchen von Szenarien zu ermöglichen, indem sie Zellenwerte ändern und die Auswirkungen der Änderungen auf die Cubedaten analysieren. Wenn Sie den Schreibzugriff für eine Partition aktivieren, können Clientanwendungen Änderungen an den Daten in der Partition aufzeichnen. Diese Änderungen, so genannte Rückschreibedaten, werden in einer separaten Tabelle gespeichert und überschreiben keine vorhandenen Daten in einer Measuregruppe. Sie werden jedoch als Teil der Cubedaten in Abfrageergebnisse einbezogen.  
  
 Sie können den Schreibzugriff für einen gesamten Cube oder nur für bestimmte Partitionen im Cube aktivieren. Dimensionen mit aktiviertem Schreibzugriff unterscheiden sich von diesen Partitionen, aber auf ergänzende Weise. Eine Partition mit aktiviertem Schreibzugriff ermöglicht den Benutzern das Update von Partitionszellen, während eine Dimension mit aktiviertem Schreibzugriff den Benutzern das Update von Dimensionselementen ermöglicht. Sie können diese zwei Funktionen auch zusammen verwenden. So muss ein Cube oder eine Partition mit aktiviertem Schreibzugriff keine Dimensionen mit aktiviertem Schreibzugriff enthalten. **Verwandte Themen: Dimensionen mit**[aktiviertem Schreib](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)Zugriff.  
  
> [!NOTE]  
>  Wenn Sie den Schreibzugriff für einen Cube aktivieren möchten, der eine Microsoft Access-Datenbank als Datenquelle verwendet, sollten Sie in den Datenquellendefinitionen des Cubes, seinen Partitionen oder seinen Dimensionen nicht Microsoft OLE DB-Anbieter für ODBC-Treiber verwenden. Stattdessen können Sie Microsoft Jet 4.0 OLE DB-Anbieter oder eine beliebige Version des Jet Service Pack, die Jet 4.0 OLE beinhaltet, verwenden. Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel [Abrufen der neuesten Service Pack für Microsoft Jet 4,0 Datenbank-Engine](https://support.microsoft.com/?kbid=239114).  
  
 Für einen Cube kann nur dann der Schreibzugriff aktiviert werden, wenn alle zugehörigen Measures die `Sum`-Aggregatfunktion verwenden. Für verknüpfte Measuregruppen und lokale Cubes kann der Schreibzugriff nicht aktiviert werden.  
  
## <a name="writeback-storage"></a>Rückschreibespeicher  
 Alle von einem Anwender des Produkts im geschäftlichen Bereich vorgenommenen Änderungen werden in der Rückschreibetabelle in Form der Abweichung vom aktuell angezeigten Wert gespeichert. Wenn ein Endbenutzer z. B. einen Zellwert von 90 auf 100 ändert, wird in der Rückschreibetabelle der Wert `+10` zusammen mit der Änderungszeit und Informationen zum ausführenden Anwender des Produkts im geschäftlichen Bereich gespeichert. Für Clientanwendungen werden die reinen Auswirkungen der gesammelten Änderungen angezeigt. Der ursprüngliche Wert im Cube bleibt erhalten, und in der Rückschreibetabelle wird eine Überwachungsliste der Änderungen aufgezeichnet.  
  
 Änderungen an Blatt- und Nichtblattzellen werden unterschiedlich gehandhabt. Eine Blattzelle stellt eine Schnittstelle zwischen einem Measure und einem Blattelement aus den einzelnen Dimensionen dar, auf die durch die Measuregruppe verwiesen wird. Der Wert einer Blattzelle wird direkt der Faktentabelle entnommen und kann nicht weiter durch einen Drilldown aufgeteilt werden. Wenn für einen Cube oder eine Partition der Schreibzugriff aktiviert wurde, können an einer Blattzelle Änderungen vorgenommen werden. Änderungen an Nichtblattzellen sind nur dann möglich, wenn die Clientanwendung einen Mechanismus bereitstellt, um die Änderungen an die Blattzellen zu verteilen, aus denen sich die Nichtblattzelle zusammensetzt. Dieser so genannte Zuordnungsprozess wird durch die UPDATE CUBE-Anweisung in MDX (Multidimensional Expressions) verwaltet. Business Intelligence-Entwickler können mithilfe der UPDATE CUBE-Anweisung Zuordnungsfunktionen integrieren. Weitere Informationen finden Sie unter [Update CUBE-Anweisung &#40;MDX-&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
> [!IMPORTANT]  
>  Wenn sich die aktualisierten Zellen nicht überlagern, kann mithilfe der `Update Isolation Level`-Eigenschaft der Verbindungszeichenfolge das Leistungsverhalten in Bezug auf UPDATE CUBE verbessert werden. Weitere Informationen finden Sie unter <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.  
  
 Unabhängig davon, ob eine Clientanwendung Änderungen verteilt, die an Nichtblattzellen vorgenommen werden, werden bei jeder Auswertung von Abfragen Änderungen in der Rückschreibetabelle sowohl auf Nichtblatt- als auch auf Blattzellwerte angewendet, sodass Anwender des Produkts im geschäftlichen Bereich die Auswirkungen der Änderungen für den gesamten Cube erkennen können.  
  
 Änderungen, die von Anwendern des Produkts im geschäftlichen Bereich vorgenommen wurden, werden in einer getrennten Rückschreibetabelle aufgezeichnet, mit der Sie wie folgt arbeiten können:  
  
-   Konvertieren einer Partition, um Änderungen dauerhaft in den Cube einzubinden. Durch diese Aktion wird der Schreibzugriff für die Measuregruppe deaktiviert. Sie können einen Filterausdruck angeben, um die Änderungen auszuwählen, die Sie konvertieren möchten.  
  
-   Verwerfen der Änderung, um die Partition in ihrem ursprünglichen Status wiederherzustellen. Durch diesen Vorgang wird der Schreibzugriff für die Partition deaktiviert.  
  
## <a name="security"></a>Sicherheit  
 Ein Anwender des Produkts im geschäftlichen Bereich darf nur dann Änderungen in der Rückschreibetabelle eines Cubes aufzeichnen, wenn er einer Rolle angehört, die über Lese-/Schreibberechtigung für die Zellen des Cubes verfügt. Sie können für jede Rolle steuern, welche Cubezellen aktualisiert werden können. Weitere Informationen finden Sie unter [Erteilen von Cube-oder Modell Berechtigungen &#40;Analysis Services&#41;](../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)   
 [Aggregationen und Aggregations Entwürfe](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Partitionen &#40;Analysis Services Mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
