---
title: Verarbeiten von Objekten (XMLA) | Microsoft Docs
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
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b4bb32d561a140746fb7b64dc9f9181f23306da9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161008"
---
# <a name="processing-objects-xmla"></a>Verarbeiten von Objekten (XMLA)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Verarbeitung den Schritt bzw. Reihe von Schritten, durch Daten in Informationen für Geschäftsanalysen umgewandelt. Die Verarbeitung ist je nach Objekttyp unterschiedlich, aber immer Teil einer Umwandlung von Daten in Informationen.  
  
 Prozess ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt können Sie die [Prozess](../xmla/xml-elements-commands/process-element-xmla.md) Befehl. Der Befehl `Process` kann die folgenden Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten:  
  
-   Cubes  
  
-   Datenbanken  
  
-   Dimensionen  
  
-   Measuregruppen  
  
-   Miningmodelle  
  
-   Miningstrukturen  
  
-   Partitionen  
  
 Um die Verarbeitung von Objekten zu kontrollieren, verfügt der Befehl `Process` über verschiedene Eigenschaften, die festgelegt werden können. Der `Process`-Befehl verfügt über Eigenschaften, die kontrollieren, wie viel Verarbeitung stattfinden wird, welche Objekte verarbeitet werden, ob Out-of-Line-Bindungen zum Einsatz kommen, wie Fehler gehandhabt und wie Rückschreibetabellen verwaltet werden.  
  
## <a name="specifying-processing-options"></a>Angeben von Verarbeitungsoptionen  
 Die [Typ](../xmla/xml-elements-properties/type-element-xmla.md) Eigenschaft von der `Process` Befehl gibt die Verarbeitungsoption zu verwenden, wenn das Objekt zu verarbeiten. Weitere Informationen zu Verarbeitungsoptionen finden Sie unter [Verarbeitungsoptionen und -einstellungen &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 In der folgenden Tabelle werden die Konstanten der Eigenschaft `Type` und die verschiedenen Objekte, die über die Konstanten verarbeitet werden können, aufgelistet.  
  
|`Type`-Wert|Anwendbare Objekte|  
|--------------------|------------------------|  
|*"ProcessFull"*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*"Processadd"*|Dimension, Partition|  
|*ProcessUpdate*|Dimension|  
|*ProcessIndexes*|Dimension, Cube, Measuregruppe, Partition|  
|*ProcessData*|Dimension, Cube, Measuregruppe, Partition|  
|*ProcessDefault*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*ProcessClear*|Cube, Datenbank, Dimension, Measuregruppe, Miningmodell, Miningstruktur, Partition|  
|*ProcessStructure*|Cube, Miningstruktur|  
|*' ProcessClearStructureOnly '*|Miningstruktur|  
|*ProcessScriptCache*|Cube|  
  
 Weitere Informationen zur Verarbeitung [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] anzuzeigen, [mehrdimensionalen Modell Objekt verarbeiten](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Angeben zu verarbeitender Objekte  
 Die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) Eigenschaft von der `Process` Befehl enthält den Objektbezeichner des Objekts, das verarbeitet werden. In einem `Process`-Befehl kann nur ein Objekt angegeben werden. Allerdings führt die Verarbeitung eines Objekts auch zur Verarbeitung aller untergeordneten Objekte. Beispielsweise werden bei der Verarbeitung einer Measuregruppe in einem Cube alle Partitionen für diese Measuregruppe verarbeitet, während bei der Verarbeitung einer Datenbank alle Objekte, die in der Datenbank enthalten sind, verarbeitet werden, einschließlich Cubes, Dimensionen und Miningstrukturen.  
  
 Wenn Sie das `ProcessAffectedObjects`-Attribut des `Process`-Befehls auf True setzen, werden alle verwandten Objekte, die von der Verarbeitung des angegebenen Objekts betroffen sind, ebenfalls verarbeitet. Angenommen, eine Dimension inkrementell aktualisiert wird, mithilfe der *ProcessUpdate* Verarbeitungsoption in der `Process` -Befehl eine Partition, deren Aggregationen für ungültig erklärt Mitglieder hinzugefügt oder gelöscht wird, ist auch verarbeitet von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Wenn `ProcessAffectedObjects` festgelegt ist auf "true". In diesem Fall kann ein einzelner `Process`-Befehl mehrere Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten, aber [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bestimmt, welche Objekte neben dem einzelnen, im `Process`-Befehl angegebenen Objekt ebenfalls verarbeitet werden müssen.  
  
 Allerdings können Sie über die `Process`-Befehle in einem `Batch`-Befehl mehrere Objekte, einschließlich Dimensionen, gleichzeitig verarbeiten. Batchvorgänge bieten eine präzisere Kontrolle über die serielle oder parallele Verarbeitung von Objekten auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, als es die Verwendung des `ProcessAffectedObjects`-Attributs tut, und ermöglicht es Ihnen, Ihren Verarbeitungsansatz für größere [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken zu optimieren. Weitere Informationen zum Ausführen von Batchvorgängen finden Sie unter [Durchführen von Batchvorgängen &#40;XMLA&#41;](performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Angeben von Out-of-Line-Bindungen  
 Wenn die `Process` Befehl nicht enthalten ist ein `Batch` Befehl, Sie können optional angeben, Out-of-Line-Bindungen in der [Bindungen](../xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../xmla/xml-elements-properties/source-element-xmla.md), und [DataSourceView-Objekt ](../xmla/xml-elements-properties/datasourceview-element-xmla.md) Eigenschaften der `Process` Befehl für die Objekte verarbeitet werden. Out-of-Line-Bindungen sind Verweise auf Datenquellen, Datenquellensichten und andere Objekte, in denen die Bindungen nur während der Ausführung des `Process`-Befehls existieren, und die vorhandene Bindungen, die dem zu verarbeitenden Objekt zugeordnet sind, überschreiben. Wenn keine Out-of-Line-Bindungen angegeben sind, werden die Bindungen verwendet, die aktuell dem zu verarbeitenden Objekt zugeordnet sind.  
  
 Out-of-Line-Bindungen werden in den folgenden Situationen verwendet:  
  
-   Inkrementelle Verarbeitung einer Partition, bei der eine alternative Faktentabelle oder ein Filter auf der vorhandenen Faktentabelle angegeben sein muss, um sicherzustellen, dass die Zeilen nicht zweimal gezählt werden.  
  
-   Mit einem Datenflusstask in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Daten bereitstellen, bei der Verarbeitung einer Dimension, die Mining-Modell oder die Partition.  
  
 Out-of-Line-Bindungen werden als Teil der Analysis Services Scripting Language (ASSL) beschrieben. Weitere Informationen über Out-of-Line-Bindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Inkrementelles Update von Partitionen  
 Das inkrementelle Update einer bereits verarbeiteten Partition erfordert in der Regel eine Out-of-Line-Bindung, da die für die Partition angegebene Bindung auf Faktentabellendaten verweist, die bereits in der Partition aggregiert wurden. Bei der inkrementellen Aktualisierung einer bereits verarbeiteten Partition über den Befehl `Process` führt  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die folgenden Aktionen aus:  
  
-   Erstellt eine temporäre Partition mit einer Struktur, die mit der Struktur der Partition identisch ist, die inkrementell aktualisiert werden soll.  
  
-   Verarbeitet die temporäre Partition über die im `Process`-Befehl angegebene Out-of-Line-Bindung.  
  
-   Führt die temporäre Partition mit der vorhandenen, ausgewählten Partition zusammen.  
  
 Weitere Informationen zum Zusammenführen von Partitionen mithilfe von XML for Analysis (XMLA) finden Sie unter [Zusammenführen von Partitionen &#40;XMLA&#41;](merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Behandeln von Verarbeitungsfehlern  
 Die [ErrorConfiguration](../xmla/xml-elements-properties/errorconfiguration-element-xmla.md) Eigenschaft von der `Process` Befehl können Sie angeben, wie Fehler bei der Verarbeitung eines Objekts behandelt werden sollen. Beispielsweise ermittelt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bei der Verarbeitung einer Dimension einen doppelten Wert in der Schlüsselspalte des Schlüsselattributs. Da Attributschlüssel eindeutig sein müssen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwirft die doppelten Datensätze. Auf der Grundlage der [KeyDuplicate](../scripting/properties/keyduplicate-element-assl.md) Eigenschaft `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] konnte:  
  
-   den Fehler ignorieren und die Verarbeitung der Dimension fortsetzen;  
  
-   eine Meldung ausgeben, die besagt, dass [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen doppelten Schlüssel ermittelt hat und die Verarbeitung fortgeführt wird.  
  
 Es gibt viele ähnliche Bedingungen, für die `ErrorConfiguration` Optionen während eines `Process`-Befehls bereitstellt.  
  
## <a name="managing-writeback-tables"></a>Verwalten von Rückschreibetabellen  
 Wenn der `Process`-Befehl eine Partition mit Schreibzugriff oder einen Cube oder eine Measuregruppe für eine derartige Partition entdeckt, die noch nicht vollständig verarbeitet ist, besteht möglicherweise noch keine Rückschreibetabelle für diese Partition. Die [WritebackTableCreation](../xmla/xml-elements-properties/writebacktablecreation-element-xmla.md) Eigenschaft von der `Process` Befehl wird bestimmt, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Rückschreibetabelle erstellen sollte.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Im folgenden Beispiel wird die [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Beispieldatenbank vollständig verarbeitet.  
  
### <a name="code"></a>Code  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 Im folgenden Beispiel wird inkrementell verarbeitet die **Internet_Sales_2004** -Partition in der **Internetverkäufe** -Measuregruppe des der **Adventure Works DW** Cube in der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Die `Process` Befehl ist fügt Aggregationen für Bestelldaten Datumsangaben nach dem 31. Dezember 2006 zur Partition mit einer Out-of-Line-abfragebindung in der `Bindings` Eigenschaft von der `Process` Befehl zum Abrufen von Zeilen der Faktentabelle aus dem generiert die Aggregationen der Partition hinzugefügt.  
  
### <a name="code"></a>Code  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
  