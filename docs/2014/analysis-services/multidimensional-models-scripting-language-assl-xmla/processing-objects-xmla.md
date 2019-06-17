---
title: Verarbeiten von Objekten (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab38ea9b58e891d813a3ca73f43d20a364275da0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727596"
---
# <a name="processing-objects-xmla"></a>Verarbeiten von Objekten (XMLA)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Verarbeitung ist der Schritt oder Reihe von Schritten, Daten in Informationen für Geschäftsanalysen umgewandelt. Die Verarbeitung ist je nach Objekttyp unterschiedlich, aber immer Teil einer Umwandlung von Daten in Informationen.  
  
 An Prozess eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekts verwenden Sie die [Prozess](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) Befehl. Der Befehl `Process` kann die folgenden Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten:  
  
-   Cubes  
  
-   Datenbanken  
  
-   Dimensionen  
  
-   Measuregruppen  
  
-   Miningmodelle  
  
-   Miningstrukturen  
  
-   Partitionen  
  
 Um die Verarbeitung von Objekten zu kontrollieren, verfügt der Befehl `Process` über verschiedene Eigenschaften, die festgelegt werden können. Der `Process`-Befehl verfügt über Eigenschaften, die kontrollieren, wie viel Verarbeitung stattfinden wird, welche Objekte verarbeitet werden, ob Out-of-Line-Bindungen zum Einsatz kommen, wie Fehler gehandhabt und wie Rückschreibetabellen verwaltet werden.  
  
## <a name="specifying-processing-options"></a>Angeben von Verarbeitungsoptionen  
 Die [Typ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) Eigenschaft der `Process` Befehl gibt die zum Verarbeiten des Objekts zu verwenden. Weitere Informationen zu Verarbeitungsoptionen finden Sie unter [Verarbeitungsoptionen und -einstellungen &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 In der folgenden Tabelle werden die Konstanten der Eigenschaft `Type` und die verschiedenen Objekte, die über die Konstanten verarbeitet werden können, aufgelistet.  
  
|`Type`-Wert|Anwendbare Objekte|  
|--------------------|------------------------|  
|*ProcessFull*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*ProcessAdd*|Dimension, Partition|  
|*ProcessUpdate*|Dimension|  
|*ProcessIndexes*|Dimension, Cube, Measuregruppe, Partition|  
|*ProcessData*|Dimension, Cube, Measuregruppe, Partition|  
|*ProcessDefault*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*ProcessClear*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*ProcessStructure*|Cube, Miningstruktur|  
|*ProcessClearStructureOnly*|Miningstruktur|  
|*ProcessScriptCache*|Cube|  
  
 Weitere Informationen zur Verarbeitung [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekten finden Sie [mehrdimensionalen Modell Objekt verarbeitet](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Angeben zu verarbeitender Objekte  
 Die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der `Process` Befehl enthält den Objektbezeichner des Objekts, das verarbeitet werden. In einem `Process`-Befehl kann nur ein Objekt angegeben werden. Allerdings führt die Verarbeitung eines Objekts auch zur Verarbeitung aller untergeordneten Objekte. Beispielsweise werden bei der Verarbeitung einer Measuregruppe in einem Cube alle Partitionen für diese Measuregruppe verarbeitet, während bei der Verarbeitung einer Datenbank alle Objekte, die in der Datenbank enthalten sind, verarbeitet werden, einschließlich Cubes, Dimensionen und Miningstrukturen.  
  
 Wenn Sie das `ProcessAffectedObjects`-Attribut des `Process`-Befehls auf True setzen, werden alle verwandten Objekte, die von der Verarbeitung des angegebenen Objekts betroffen sind, ebenfalls verarbeitet. Angenommen, eine Dimension inkrementell aktualisiert wird, mithilfe der *ProcessUpdate* Verarbeitungsoption in der `Process` -Befehl eine Partition, deren Aggregationen für ungültig erklärt Mitglieder hinzugefügt oder gelöscht wird, ist auch von verarbeitet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Wenn `ProcessAffectedObjects` wird festgelegt auf "true". In diesem Fall kann ein einzelner `Process`-Befehl mehrere Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten, aber [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bestimmt, welche Objekte neben dem einzelnen, im `Process`-Befehl angegebenen Objekt ebenfalls verarbeitet werden müssen.  
  
 Allerdings können Sie über die `Process`-Befehle in einem `Batch`-Befehl mehrere Objekte, einschließlich Dimensionen, gleichzeitig verarbeiten. Batchvorgänge bieten eine präzisere Kontrolle über die serielle oder parallele Verarbeitung von Objekten auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, als es die Verwendung des `ProcessAffectedObjects`-Attributs tut, und ermöglicht es Ihnen, Ihren Verarbeitungsansatz für größere [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken zu optimieren. Weitere Informationen zum Ausführen von Batchvorgängen finden Sie unter [Ausführen von Batchvorgängen &#40;XMLA&#41;](performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Angeben von Out-of-Line-Bindungen  
 Wenn die `Process` Befehl befindet sich nicht von einer `Batch` Befehl können Sie optional Out-of-Line-Bindungen im Angeben der [Bindungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), und [DataSourceView-Objekt ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) Eigenschaften der `Process` Befehl für die Objekte verarbeitet werden. Out-of-Line-Bindungen sind Verweise auf Datenquellen, Datenquellensichten und andere Objekte, in denen die Bindungen nur während der Ausführung des `Process`-Befehls existieren, und die vorhandene Bindungen, die dem zu verarbeitenden Objekt zugeordnet sind, überschreiben. Wenn keine Out-of-Line-Bindungen angegeben sind, werden die Bindungen verwendet, die aktuell dem zu verarbeitenden Objekt zugeordnet sind.  
  
 Out-of-Line-Bindungen werden in den folgenden Situationen verwendet:  
  
-   Inkrementelle Verarbeitung einer Partition, bei der eine alternative Faktentabelle oder ein Filter auf der vorhandenen Faktentabelle angegeben sein muss, um sicherzustellen, dass die Zeilen nicht zweimal gezählt werden.  
  
-   Mit einem Datenflusstask in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Daten bereitstellen, während der Verarbeitung einer Dimension, die Mining-Modell oder die Partition.  
  
 Out-of-Line-Bindungen werden als Teil der Analysis Services Scripting Language (ASSL) beschrieben. Weitere Informationen zur Out-of-Line-Bindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Inkrementelles Update von Partitionen  
 Das inkrementelle Update einer bereits verarbeiteten Partition erfordert in der Regel eine Out-of-Line-Bindung, da die für die Partition angegebene Bindung auf Faktentabellendaten verweist, die bereits in der Partition aggregiert wurden. Bei der inkrementellen Aktualisierung einer bereits verarbeiteten Partition über den Befehl `Process` führt  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die folgenden Aktionen aus:  
  
-   Erstellt eine temporäre Partition mit einer Struktur, die mit der Struktur der Partition identisch ist, die inkrementell aktualisiert werden soll.  
  
-   Verarbeitet die temporäre Partition über die im `Process`-Befehl angegebene Out-of-Line-Bindung.  
  
-   Führt die temporäre Partition mit der vorhandenen, ausgewählten Partition zusammen.  
  
 Weitere Informationen zum Zusammenführen von Partitionen mithilfe von XML for Analysis (XMLA) verwenden, finden Sie unter [Zusammenführen von Partitionen &#40;XMLA&#41;](merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Behandeln von Verarbeitungsfehlern  
 Die [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) Eigenschaft der `Process` Befehl können Sie angeben, wie Fehler bei der Verarbeitung eines Objekts behandelt. Beispielsweise ermittelt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bei der Verarbeitung einer Dimension einen doppelten Wert in der Schlüsselspalte des Schlüsselattributs. Da Attributschlüssel eindeutig sein müssen, verwirft [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die doppelten Datensätze. Auf der Grundlage der [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) Eigenschaft `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] konnte:  
  
-   den Fehler ignorieren und die Verarbeitung der Dimension fortsetzen;  
  
-   eine Meldung ausgeben, die besagt, dass [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen doppelten Schlüssel ermittelt hat und die Verarbeitung fortgeführt wird.  
  
 Es gibt viele ähnliche Bedingungen, für die `ErrorConfiguration` Optionen während eines `Process`-Befehls bereitstellt.  
  
## <a name="managing-writeback-tables"></a>Verwalten von Rückschreibetabellen  
 Wenn der `Process`-Befehl eine Partition mit Schreibzugriff oder einen Cube oder eine Measuregruppe für eine derartige Partition entdeckt, die noch nicht vollständig verarbeitet ist, besteht möglicherweise noch keine Rückschreibetabelle für diese Partition. Die [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) Eigenschaft der `Process` Befehl wird bestimmt, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Rückschreibetabelle erstellen sollte.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Im folgenden Beispiel wird die [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Beispieldatenbank vollständig verarbeitet.  
  
### <a name="code"></a>Code  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird inkrementell verarbeitet die **Internet_Sales_2004** partition im der **Internetverkäufe** -Measuregruppe des der **Adventure Works DW** Cube in der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Die `Process` -Befehl fügt Aggregationen für Bestelldaten Datumsangaben nach dem 31. Dezember 2006 zur Partition mit einer Out-of-Line-abfragebindung in der `Bindings` Eigenschaft der `Process` Befehl aus, um die Zeilen der Faktentabelle aus der Erstellung abrufen die Aggregationen der Partition hinzugefügt.  
  
### <a name="code"></a>Code  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
