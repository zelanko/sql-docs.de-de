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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727596"
---
# <a name="processing-objects-xmla"></a>Verarbeiten von Objekten (XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ist die Verarbeitung der Schritt oder eine Reihe von Schritten, durch die Daten in Informationen für Geschäftsanalysen umgewandelt werden. Die Verarbeitung ist je nach Objekttyp unterschiedlich, aber immer Teil einer Umwandlung von Daten in Informationen.  
  
 Zum Verarbeiten eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekts können Sie den [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) -Befehl verwenden. Der Befehl `Process` kann die folgenden Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten:  
  
-   Cubes  
  
-   Datenbanken  
  
-   Dimensionen  
  
-   Measuregruppen  
  
-   Miningmodelle  
  
-   Miningstrukturen  
  
-   Partitionen  
  
 Um die Verarbeitung von Objekten zu kontrollieren, verfügt der Befehl `Process` über verschiedene Eigenschaften, die festgelegt werden können. Der `Process`-Befehl verfügt über Eigenschaften, die kontrollieren, wie viel Verarbeitung stattfinden wird, welche Objekte verarbeitet werden, ob Out-of-Line-Bindungen zum Einsatz kommen, wie Fehler gehandhabt und wie Rückschreibetabellen verwaltet werden.  
  
## <a name="specifying-processing-options"></a>Angeben von Verarbeitungsoptionen  
 Die [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) -Eigenschaft des `Process` -Befehls gibt die Verarbeitungsoption an, die bei der Verarbeitung des-Objekts verwendet werden soll. Weitere Informationen zu Verarbeitungsoptionen finden Sie unter [Verarbeitungsoptionen und -einstellungen &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 In der folgenden Tabelle werden die Konstanten der Eigenschaft `Type` und die verschiedenen Objekte, die über die Konstanten verarbeitet werden können, aufgelistet.  
  
|Wert vom Typ `Type`|Anwendbare Objekte|  
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
  
 Weitere Informationen zum verarbeiten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] von Objekten finden Sie unter mehr [dimensionale Modell Objekt Verarbeitung](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Angeben zu verarbeitender Objekte  
 Die [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Eigenschaft des `Process` -Befehls enthält den Objekt Bezeichner des zu verarbeitenden Objekts. In einem `Process`-Befehl kann nur ein Objekt angegeben werden. Allerdings führt die Verarbeitung eines Objekts auch zur Verarbeitung aller untergeordneten Objekte. Beispielsweise werden bei der Verarbeitung einer Measuregruppe in einem Cube alle Partitionen für diese Measuregruppe verarbeitet, während bei der Verarbeitung einer Datenbank alle Objekte, die in der Datenbank enthalten sind, verarbeitet werden, einschließlich Cubes, Dimensionen und Miningstrukturen.  
  
 Wenn Sie das `ProcessAffectedObjects`-Attribut des `Process`-Befehls auf True setzen, werden alle verwandten Objekte, die von der Verarbeitung des angegebenen Objekts betroffen sind, ebenfalls verarbeitet. Wenn beispielsweise eine Dimension inkrementell mithilfe der Verarbeitungsoption *ProcessUpdate* im `Process` Befehl aktualisiert wird, wird jede Partition, deren Aggregationen aufgrund von hinzugefügten oder gelöschten Membern ungültig werden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , `ProcessAffectedObjects` auch von verarbeitet, wenn auf true festgelegt ist. In diesem Fall kann ein einzelner `Process`-Befehl mehrere Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz verarbeiten, aber [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bestimmt, welche Objekte neben dem einzelnen, im `Process`-Befehl angegebenen Objekt ebenfalls verarbeitet werden müssen.  
  
 Allerdings können Sie über die `Process`-Befehle in einem `Batch`-Befehl mehrere Objekte, einschließlich Dimensionen, gleichzeitig verarbeiten. Batchvorgänge bieten eine präzisere Kontrolle über die serielle oder parallele Verarbeitung von Objekten auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, als es die Verwendung des `ProcessAffectedObjects`-Attributs tut, und ermöglicht es Ihnen, Ihren Verarbeitungsansatz für größere [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken zu optimieren. Weitere Informationen zum Ausführen von Batch Vorgängen finden Sie unter Ausführen von Batch Vorgängen [&#40;XMLA&#41;](performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Angeben von Out-of-Line-Bindungen  
 Wenn der `Process` Befehl nicht `Batch` in einem Befehl enthalten ist, können Sie optional out-of-Line-Bindungen in den Eigenschaften [Bindungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)und [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) des `Process` Befehls für die zu verarbeitenden Objekte angeben. Out-of-Line-Bindungen sind Verweise auf Datenquellen, Datenquellensichten und andere Objekte, in denen die Bindungen nur während der Ausführung des `Process`-Befehls existieren, und die vorhandene Bindungen, die dem zu verarbeitenden Objekt zugeordnet sind, überschreiben. Wenn keine Out-of-Line-Bindungen angegeben sind, werden die Bindungen verwendet, die aktuell dem zu verarbeitenden Objekt zugeordnet sind.  
  
 Out-of-Line-Bindungen werden in den folgenden Situationen verwendet:  
  
-   Inkrementelle Verarbeitung einer Partition, bei der eine alternative Faktentabelle oder ein Filter auf der vorhandenen Faktentabelle angegeben sein muss, um sicherzustellen, dass die Zeilen nicht zweimal gezählt werden.  
  
-   Verwenden eines Datenfluss Tasks in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] zum Bereitstellen von Daten bei der Verarbeitung einer Dimension, eines Mining Modells oder einer Partition.  
  
 Out-of-Line-Bindungen werden als Teil der Analysis Services Scripting Language (ASSL) beschrieben. Weitere Informationen zu out-of-Line-Bindungen in ASSL finden Sie unter [Datenquellen und Bindungen &#40;mehrdimensionalen SSAS-&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Inkrementelles Update von Partitionen  
 Das inkrementelle Update einer bereits verarbeiteten Partition erfordert in der Regel eine Out-of-Line-Bindung, da die für die Partition angegebene Bindung auf Faktentabellendaten verweist, die bereits in der Partition aggregiert wurden. Bei der inkrementellen Aktualisierung einer bereits verarbeiteten Partition über den Befehl `Process` führt  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die folgenden Aktionen aus:  
  
-   Erstellt eine temporäre Partition mit einer Struktur, die mit der Struktur der Partition identisch ist, die inkrementell aktualisiert werden soll.  
  
-   Verarbeitet die temporäre Partition über die im `Process`-Befehl angegebene Out-of-Line-Bindung.  
  
-   Führt die temporäre Partition mit der vorhandenen, ausgewählten Partition zusammen.  
  
 Weitere Informationen zum Zusammenführen von Partitionen mithilfe von XML for Analysis (XMLA) finden Sie unter Zusammenführen von [Partitionen &#40;XMLA&#41;](merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Behandeln von Verarbeitungsfehlern  
 Mit der [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) -Eigenschaft `Process` des-Befehls können Sie angeben, wie Fehler behandelt werden sollen, die bei der Verarbeitung eines Objekts aufgetreten sind. Beispielsweise ermittelt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bei der Verarbeitung einer Dimension einen doppelten Wert in der Schlüsselspalte des Schlüsselattributs. Da Attributschlüssel eindeutig sein müssen, verwirft [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die doppelten Datensätze. Basierend auf der [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) -Eigenschaft `ErrorConfiguration`von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] könnte Folgendes:  
  
-   den Fehler ignorieren und die Verarbeitung der Dimension fortsetzen;  
  
-   eine Meldung ausgeben, die besagt, dass [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] einen doppelten Schlüssel ermittelt hat und die Verarbeitung fortgeführt wird.  
  
 Es gibt viele ähnliche Bedingungen, für die `ErrorConfiguration` Optionen während eines `Process`-Befehls bereitstellt.  
  
## <a name="managing-writeback-tables"></a>Verwalten von Rückschreibetabellen  
 Wenn der `Process`-Befehl eine Partition mit Schreibzugriff oder einen Cube oder eine Measuregruppe für eine derartige Partition entdeckt, die noch nicht vollständig verarbeitet ist, besteht möglicherweise noch keine Rückschreibetabelle für diese Partition. Die Eigenschaft " [schreitebacktablecreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) " `Process` des Befehls bestimmt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ob eine Rück schreibe Tabelle erstellen soll.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird die [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Beispieldatenbank vollständig verarbeitet.  
  
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
  
### <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel wird die **Internet_Sales_2004** Partition in der **Internet Sales** -Measure-Gruppe des **Adventure Works DW** -Cubes in der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] - [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Beispieldatenbank inkrementell verarbeitet. Der `Process` Befehl fügt Aggregationen für Bestelldaten nach dem 31. Dezember 2006 zur Partition hinzu, indem eine Out-of-Line-Abfrage Bindung in `Bindings` der-Eigenschaft `Process` des-Befehls verwendet wird, um die Fakten Tabellenzeilen abzurufen, aus denen Aggregationen generiert werden, die der Partition hinzugefügt werden sollen.  
  
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
  
  
