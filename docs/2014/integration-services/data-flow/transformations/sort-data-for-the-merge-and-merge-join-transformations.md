---
title: Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f8ced7cfaef647fb8aaa93a477c69f1d690d0328
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213450"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin
  In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]erfordern die Transformationen für Zusammenführen und Zusammenführungsjoin sortierte Daten für ihre Eingaben. Die Eingabedaten müssen physisch sortiert werden, und die Sortierungsoptionen müssen für die Ausgaben und die Ausgabespalten in der Quelle oder Upstreamtransformation festgelegt werden. Wenn die Sortierungsoptionen anzeigen, dass die Daten sortiert sind, dies jedoch in Wirklichkeit nicht der Fall ist, sind die Ergebnisse des Vorgangs der Zusammenführung oder des Zusammenführungsjoins nicht vorhersagbar.  
  
## <a name="sorting-the-data"></a>Sortieren der Daten  
 Sie können diese Daten auch mithilfe einer der folgenden Methoden sortieren:  
  
-   Verwenden Sie in der Quelle eine ORDER BY-Klausel in der Anweisung, die zum Laden der Daten verwendet wird.  
  
-   Fügen Sie im Datenfluss vor der Transformation für Zusammenführung oder dem Zusammenführungsjoin eine Transformation zum Sortieren ein.  
  
 Wenn es sich bei den Daten um Zeichenfolgendaten handelt, erwartet sowohl die Transformation für Zusammenführung als auch die für den Zusammenführungsjoin, dass die Zeichenfolgenwerte mithilfe der Windows-Sortierung sortiert wurden. Führen Sie die folgenden Vorgänge aus, um Zeichenfolgenwerte für die Transformationen für Zusammenführung und für den Zusammenführungsjoin bereitzustellen, die mithilfe der Windows-Sortierung sortiert wurden.  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>So stellen Sie mithilfe der Windows-Sortierung sortierte Zeichenfolgenwerte bereit  
  
-   Sortieren Sie die Daten mit einer Transformation zum Sortieren.  
  
     Die Transformation zum Sortieren verwendet die Windows-Sortierung, um Zeichenfolgenwerte zu sortieren.  
  
     – oder –  
  
-   Verwenden Sie den Transact-SQL-Umwandlungsoperator, um die `varchar`-Werte zuerst in `nvarchar`-Werte umzuwandeln, und sortieren Sie die Daten anschließend mit der ORDER BY-Klausel in Transact-SQL.  
  
    > [!IMPORTANT]  
    >  Die ORDER BY-Klausel allein reicht nicht aus, da sie eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sortierung zum Sortieren der Zeichenfolgenwerte verwendet. Mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sortierung ergibt sich möglicherweise eine andere Sortierreihenfolge als mit der Windows-Sortierung. Dadurch könnte die Transformation für Zusammenführung und für Zusammenführungsjoin zu unerwarteten Ergebnissen führen.  
  
## <a name="setting-sort-options-on-the-data"></a>Festlegen von Sortieroptionen für die Daten  
 Es gibt zwei wichtige Sortiereigenschaften, die für die Quelle oder die Upstreamtransformation festgelegt werden müssen, die die Daten für Transformationen für Zusammenführen und für Zusammenführungsjoin bereitstellen.  
  
-   Die `IsSorted`-Eigenschaft der Ausgabe, die angibt, ob die Daten sortiert wurden. Diese Eigenschaft muss festgelegt werden, um `True`.  
  
    > [!IMPORTANT]  
    >  Festlegen des Werts von der `IsSorted` Eigenschaft `True` werden die Daten nicht sortiert. Diese Eigenschaft ist lediglich ein Hinweis für die Downstreamkomponenten, dass die Daten vorher sortiert wurden.  
  
-   Die `SortKeyPosition` -Eigenschaft der Ausgabespalten, der angibt, ob eine Spalte sortiert ist, Sortierreihenfolge der Spalte und die Sequenz, die in der mehrere Spalten sortiert werden. Diese Eigenschaft muss für jede Spalte sortierter Daten festgelegt werden.  
  
 Wenn Sie zum Sortieren der Daten eine Transformation zum Sortieren verwenden, legt die Transformation zum Sortieren diese beiden von der Transformation für Zusammenführen und für Zusammenführungsjoin verlangten Eigenschaften fest. Also die Transformation zum Sortieren legt die `IsSorted` -Eigenschaft ihrer Ausgabe auf `True`, und legt die `SortKeyPosition` Eigenschaften ihrer Ausgabespalten.  
  
 Wenn Sie zum Sortieren der Daten jedoch keine Transformation zum Sortieren verwenden, müssen Sie diese Sortiereigenschaften für die Quelle oder die Upstreamtransformation manuell festlegen. Verwenden Sie folgendes Verfahren, um die Sortiereigenschaften für die Quelle oder Upstreamtransformation manuell festzulegen.  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>So legen Sie Sortierattribute für eine Quelle oder Transformationskomponente manuell fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Suchen Sie auf der Registerkarte **Datenfluss** nach der entsprechenden Quelle oder Upstreamtransformation, oder ziehen Sie diese von der **Toolbox** auf die Entwurfsoberfläche.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Komponente, und klicken Sie auf **Erweiterten Editor anzeigen**.  
  
5.  Klicken Sie auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** .  
  
6.  Klicken Sie auf  **\<Komponentenname > Ausgabe**, und legen Sie die `IsSorted` Eigenschaft `True`.  
  
    > [!NOTE]  
    >  Wenn Sie manuell festlegen der `IsSorted` -Eigenschaft der Ausgabe um `True` und die Daten nicht sortiert ist, gibt es möglicherweise Vergleichsvorgängen mit fehlenden oder beschädigten Daten kommen in der downstreamtransformation für Zusammenführung oder des Zusammenführungsjoins beim Ausführen des Pakets.  
  
7.  Erweitern Sie **Ausgabespalten**.  
  
8.  Klicken Sie auf die Spalte, die Sie angeben möchten, sortiert ist, und legen Sie dessen `SortKeyPosition` Eigenschaft, um ein ganze Zahl ungleich NULL-Wert, durch die folgenden Richtlinien halten:  
  
    -   Der ganzzahlige Wert muss eine numerische Sequenz darstellen, die bei 1 beginnt und sich jeweils um 1 erhöht.  
  
    -   Ein positiver ganzzahliger Wert gibt eine aufsteigende Sortierreihenfolge an.  
  
    -   Ein negativer ganzzahliger Wert gibt eine absteigende Sortierreihenfolge an. (Wenn eine negative Zahl angegeben wird, legt der absolute Wert der Zahl die Position der Spalte in der Sortierreihenfolge fest.)  
  
    -   Der Standardwert 0 gibt an, dass die Spalte nicht sortiert ist. Lassen Sie den Wert 0 für Ausgabespalten unverändert, die kein Bestandteil der Sortierung sind.  
  
     Beachten Sie als Beispiel für die Festlegung der `SortKeyPosition`-Eigenschaft folgende Transact-SQL-Anweisung, die Daten in eine Quelle lädt:  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     Legen Sie für diese Anweisung, die `SortKeyPosition` -Eigenschaft für jede Spalte folgendermaßen:  
  
    -   Legen Sie die `SortKeyPosition`-Eigenschaft von ColumnA auf 1 fest. Dies gibt an, dass ColumnA die erste Spalte ist, die sortiert wird, und dass sie in aufsteigender Reihenfolge sortiert wird.  
  
    -   Legen Sie die `SortKeyPosition`-Eigenschaft von ColumnB auf -2 fest. Dies gibt an, dass ColumnB die zweite Spalte ist, die sortiert wird, und dass sie in absteigender Reihenfolge sortiert wird.  
  
    -   Legen Sie die `SortKeyPosition` -Eigenschaft von ColumnC auf 3. Dies gibt an, dass ColumnC die dritte Spalte ist, die sortiert wird, und dass sie in aufsteigender Reihenfolge sortiert wird.  
  
9. Wiederholen Sie Schritt 8 für jede sortierte Spalte.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Transformation für zusammenführen](merge-transformation.md)   
 [Transformation für Zusammenführungsjoin](merge-join-transformation.md)   
 [Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [Datenflusstask] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  
