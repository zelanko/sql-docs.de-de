---
title: Erstellen und Ändern von Objekten (XMLA) | Microsoft Docs
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
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9702046c3e3c9e9ab0e9ff525d832baf611fe4b9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047285"
---
# <a name="creating-and-altering-objects-xmla"></a>Erstellen und Ändern von Objekten (XMLA)
  Hauptobjekte können unabhängig erstellt, geändert und gelöscht werden. Zu den Hauptobjekten gehören die folgenden Objekte:  
  
-   Server  
  
-   Datenbanken  
  
-   Dimensionen  
  
-   Cubes  
  
-   Measuregruppen  
  
-   Partitionen  
  
-   Perspektiven  
  
-   Miningmodelle  
  
-   Rollen  
  
-   Einem Server oder einer Datenbank zugeordnete Befehle  
  
-   Datenquellen  
  
 Verwenden Sie die [erstellen](../xmla/xml-elements-commands/create-element-xmla.md) Befehl zum Erstellen von ein Hauptobjekt auf einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], und die [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) Befehl aus, um ein vorhandenes Objekt auf einer Instanz zu ändern. Beide Befehle werden ausgeführt, mit der [Execute](../xmla/xml-elements-methods-execute.md) Methode.  
  
## <a name="creating-objects"></a>Erstellen von Objekten  
 Wenn Sie Objekte über die `Create`-Methode erstellen, müssen Sie zunächst das übergeordnete Objekt identifizieren, das das zu erstellende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt enthält. Bestimmen Sie das übergeordnete Objekt durch die Bereitstellung eines Objektverweis in der [ParentObject](../xmla/xml-elements-properties/object-element-xmla.md) Eigenschaft von der `Create` Befehl. Jeder Objektverweis enthält die Objektbezeichner, die notwendig sind, um das übergeordnete Objekt für den `Create`-Befehl zu identifizieren. Weitere Informationen über Objektverweise finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](../xmla/xml-elements-objects.md).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um eine neue Measuregruppe für den Cube zu erstellen. Der Objektverweis für den Cube in der Eigenschaft `ParentObject` enthält sowohl einen Datenbankbezeichner als auch einen Cubebezeichner, da der gleiche Cubebezeichner potenziell von einer anderen Datenbank verwendet werden könnte.  
  
 Die [ObjectDefinition](../xmla/xml-elements-properties/objectdefinition-element-xmla.md) Element enthält Analysis Services Scripting Language (ASSL)-Elemente, die definieren, das Hauptobjekt erstellt werden soll. Weitere Informationen über ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Wenn Sie das `AllowOverwrite`-Attribut des `Create`-Befehls auf True setzen, können Sie ein vorhandenes Hauptobjekt mit dem gleichen Bezeichner überschreiben. Andernfalls tritt ein Fehler auf, wenn im übergeordneten Objekt bereits ein Hauptobjekt mit dem gleichen Bezeichner vorhanden ist.  
  
 Weitere Informationen zu den `Create` Befehl, finden Sie unter [Element erstellen &#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md).  
  
### <a name="creating-session-objects"></a>Erstellen von Sitzungsobjekten  
 Sitzungsobjekte sind temporäre Objekte, die nur für die explizite oder implizierte Sitzung zur Verfügung stehen, die von einer Clientanwendung verwendet werden. Bei Beendigung der Sitzung werden diese gelöscht. Sie können Sitzungsobjekte erstellen, durch Festlegen der `Scope` Attribut von der `Create` -Befehls auf *Sitzung*.  
  
> [!NOTE]  
>  Bei Verwendung der *Sitzung* festlegen, die `ObjectDefinition` Element darf nur [Dimension](../scripting/objects/dimension-element-assl.md), [Cube](../scripting/objects/cube-element-assl.md), oder [MiningModel](../scripting/objects/miningmodel-element-assl.md) ASSL Elemente.  
  
## <a name="altering-objects"></a>Ändern von Objekten  
 Bei Änderung von Objekten über die `Alter` -Methode, müssen Sie zunächst das Objekt, das geändert werden, indem Sie einen Objektverweis in identifizieren die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) Eigenschaft von der `Alter` Befehl. Jeder Objektverweis enthält die Objektbezeichner, die notwendig sind, um das Objekt für den `Alter`-Befehl zu identifizieren. Weitere Informationen über Objektverweise finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](../xmla/xml-elements-objects.md).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um die Struktur eines Cubes zu ändern. Der Objektverweis für den Cube in der Eigenschaft `Object` enthält sowohl einen Datenbankbezeichner als auch einen Cubebezeichner, da der gleiche Cubebezeichner potenziell von einer anderen Datenbank verwendet werden könnte.  
  
 Das `ObjectDefinition`-Element enthält ASSL-Elemente, die das Hauptobjekt definieren, das geändert werden soll. Weitere Informationen über ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Wenn Sie das `AllowCreate`-Attribut des `Alter`-Befehls auf True setzen, können Sie das angegebene Hauptobjekt erstellen, wenn das Objekt nicht existiert. Andernfalls tritt ein Fehler auf, wenn ein angegebenes Hauptobjekt nicht bereits vorhanden ist.  
  
### <a name="using-the-objectexpansion-attribute"></a>Verwenden des ObjectExpansion-Attributs  
 Wenn Sie nur die Eigenschaften des Hauptobjekts ändern und sind nicht nebenobjekte, die im Hauptobjekt enthalten sind, legen Sie die `ObjectExpansion` Attribut von der `Alter` -Befehls auf *' ObjectProperties '*. Die `ObjectDefinition`-Eigenschaft muss dann nur die Elemente für die Eigenschaften des Hauptobjekts enthalten, und der `Alter`-Befehl lässt die zum Hauptobjekt gehörenden Nebenobjekte unverändert.  
  
 Um nebenobjekte für ein Hauptobjekt neu definieren, müssen Sie festlegen, die `ObjectExpansion` -Attribut *ExpandFull* und die Objektdefinition muss alle nebenobjekte sind Objekte, die im Hauptobjekt enthalten sind enthalten. Wenn die `ObjectDefinition`-Eigenschaft des `Alter`-Befehls nicht explizit ein im Hauptobjekt enthaltenes Nebenobjekt einbindet, wird das nicht eingebundene Nebenobjekt gelöscht.  
  
### <a name="altering-session-objects"></a>Ändern von Sitzungsobjekten  
 So ändern Sie die Session-Objekte erstellt, indem die `Create` Befehl, legen die `Scope` Attribut von der `Alter` -Befehls auf *Sitzung*.  
  
> [!NOTE]  
>  Bei Verwendung der *Sitzung* festlegen, die `ObjectDefinition` Element darf nur [Dimension](../scripting/objects/dimension-element-assl.md), [Cube](../scripting/objects/cube-element-assl.md), oder [MiningModel](../scripting/objects/miningmodel-element-assl.md) ASSL Elemente.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Erstellen oder Ändern von untergeordneten Objekten  
 Obwohl ein `Create`- oder  `Alter`-Befehl nur das oberste Hauptobjekt erstellt oder ändert, kann das Hauptobjekt, das erstellt oder geändert wird, Definitionen innerhalb der einschließenden `ObjectDefinition`-Eigenschaft für andere Haupt- und Nebenobjekte enthalten, die ihm untergeordnet sind. Beispielsweise geben Sie bei der Definition eines Cubes die übergeordnete Datenbank in `ParentObject` an, und innerhalb der Cubedefinition in `ObjectDefinition` können Sie Measuregruppen für den Cube erstellen, und innerhalb der Measuregruppen können Sie Partitionen für jede Measuregruppe definieren. Ein Nebenobjekt kann nur unter dem Hauptobjekt definiert werden, das es enthält. Weitere Informationen über Haupt-und nebenobjekte finden Sie unter [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Das folgende Beispiel erstellt eine relationale Datenquelle, verweist der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
### <a name="code"></a>Code  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Description  
 Im folgenden Beispiel wird die im vorherigen Beispiel erzeugte relationale Datenquelle so geändert, dass der Abfragetimeout der Datenquelle nach 30 Sekunden einsetzt.  
  
### <a name="code"></a>Code  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>Kommentare  
 Die `ObjectExpansion` Attribut von der `Alter` Befehlssatz wurde um *' ObjectProperties '*. Mit dieser Einstellung kann die [ImpersonationInfo](../scripting/properties/impersonationinfo-element-assl.md) -Element, ein nebenobjekt aus der Datenquelle, die in definierten Auszuschließendes `ObjectDefinition`. Daher bleiben die Informationen zum Identitätswechsel für die Datenquelle auf "Service Account" festgelegt, wie es im ersten Beispiel angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Execute-Methode &#40;XMLA&#41;](../xmla/xml-elements-methods-execute.md)   
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  