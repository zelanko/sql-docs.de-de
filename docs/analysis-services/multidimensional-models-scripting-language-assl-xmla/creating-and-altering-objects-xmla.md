---
title: Erstellen und Ändern von Objekten (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86f52c2ea61b8b62ea9bfe5ffe6b3c7b06977740
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145145"
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
  
 Sie verwenden die [erstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) Befehl aus, um ein Hauptobjekt auf einer Instanz von erstellen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], und die [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) Befehl aus, um ein vorhandenes Objekt auf einer Instanz zu ändern. Beide Befehle werden ausgeführt, mit der [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) Methode.  
  
## <a name="creating-objects"></a>Erstellen von Objekten  
 Wenn Sie Objekte erstellen, mit der **erstellen** -Methode müssen Sie zunächst das übergeordnete Objekt, das enthält identifizieren die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zu erstellenden Objekts. Identifizieren Sie das übergeordnete Objekt durch die Bereitstellung eines Objektverweis in der [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der **erstellen** Befehl. Jeder Objektverweis enthält die Objektbezeichner, die erforderlich sind, zur eindeutigen Identifizierung für das übergeordnete Objekt für die **erstellen** Befehl. Weitere Informationen über Objektverweise finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um eine neue Measuregruppe für den Cube zu erstellen. Der Objektverweis für den Cube in der **ParentObject** Eigenschaft enthält sowohl einen Datenbankbezeichner als auch einen cubebezeichner, da der gleiche cubebezeichner potenziell von einer anderen Datenbank verwendet werden kann.  
  
 Die [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) Element enthält Analysis Services Scripting Language (ASSL)-Elemente, die definieren, das Hauptobjekt erstellt werden. Weitere Informationen über ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Setzen Sie die **AllowOverwrite** Attribut der **erstellen** Befehls auf "true", Sie können ein vorhandenes Hauptobjekt mit dem angegebenen Bezeichner überschreiben. Andernfalls tritt ein Fehler auf, wenn im übergeordneten Objekt bereits ein Hauptobjekt mit dem gleichen Bezeichner vorhanden ist.  
  
 Weitere Informationen zu den **erstellen** Befehl, finden Sie unter [Element erstellen &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).  
  
### <a name="creating-session-objects"></a>Erstellen von Sitzungsobjekten  
 Sitzungsobjekte sind temporäre Objekte, die nur für die explizite oder implizierte Sitzung zur Verfügung stehen, die von einer Clientanwendung verwendet werden. Bei Beendigung der Sitzung werden diese gelöscht. Sie können Sitzungsobjekte erstellen, durch Festlegen der **Bereich** Attribut der **erstellen** Befehl *Sitzung*.  
  
> [!NOTE]  
>  Bei Verwendung der *Sitzung* festlegen, die **ObjectDefinition** Element darf nur [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), oder [ MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL-Elemente.  
  
## <a name="altering-objects"></a>Ändern von Objekten  
 Beim Ändern von Objekten mithilfe der **Alter** -Methode müssen Sie zunächst das Objekt, das geändert werden, durch die Bereitstellung eines Objektverweis in identifizieren die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der **Alter**Befehl. Jeder Objektverweis enthält die Objektbezeichner erforderlich, um die Identifizierung des Objekts für die **Alter** Befehl. Weitere Informationen über Objektverweise finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um die Struktur eines Cubes zu ändern. Der Objektverweis für den Cube in der **Objekt** Eigenschaft enthält sowohl einen Datenbankbezeichner als auch einen cubebezeichner, da der gleiche cubebezeichner potenziell von einer anderen Datenbank verwendet werden kann.  
  
 Die **ObjectDefinition** -Element enthält ASSL-Elemente, die zu ändernden Hauptobjekts definieren. Weitere Informationen über ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Setzen Sie die **AllowCreate** Attribut der **Alter** Befehls auf "true", Sie können das angegebene Hauptobjekt erstellen, wenn das Objekt nicht vorhanden ist. Andernfalls tritt ein Fehler auf, wenn ein angegebenes Hauptobjekt nicht bereits vorhanden ist.  
  
### <a name="using-the-objectexpansion-attribute"></a>Verwenden des ObjectExpansion-Attributs  
 Wenn Sie nur die Eigenschaften des Hauptobjekts ändern und sind nicht nebenobjekte, die im Hauptobjekt enthalten sind, legen Sie die **ObjectExpansion** Attribut des der **Alter** Befehl *ObjectProperties*. Die **ObjectDefinition** hat Eigenschaft klicken Sie dann nur die Elemente für die Eigenschaften des Hauptobjekts, enthalten und die **Alter** Befehl bewirkt, dass im unverändert Hauptobjekt gehörenden nebenobjekte.  
  
 Um nebenobjekte für ein Hauptobjekt neu zu definieren, müssen Sie festlegen, die **ObjectExpansion** Attribut *ExpandFull* und die Objektdefinition muss alle nebenobjekte, die im Hauptobjekt enthalten sind enthalten. Wenn die **ObjectDefinition** Eigenschaft der **Alter** -Befehl schließt keine explizit ein nebenobjekt aus, die im Hauptobjekt enthalten ist, wird gelöscht, das kleinere Objekt, das nicht enthalten ist.  
  
### <a name="altering-session-objects"></a>Ändern von Sitzungsobjekten  
 Session-Objekte erstellt, durch Ändern der **erstellen** Befehl, legen die **Bereich** Attribut der **Alter** Befehl *Sitzung*.  
  
> [!NOTE]  
>  Bei Verwendung der *Sitzung* festlegen, die **ObjectDefinition** Element darf nur [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), oder [ MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL-Elemente.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Erstellen oder Ändern von untergeordneten Objekten  
 Obwohl eine **erstellen** oder **Alter** Befehl erstellt oder ändert Sie nur eine oberste Hauptobjekt, das Hauptobjekt, das erstellt oder geändert wird, kann Definitionen innerhalb der einschließenden enthalten  **ObjectDefinition** -Eigenschaft für andere Haupt- und Nebenversionsnummern-Objekte, die, die ihm untergeordnet sind. Z. B. Wenn Sie einen Cube definieren, geben Sie die übergeordnete Datenbank in **ParentObject**, und innerhalb der Cubedefinition in **ObjectDefinition** können Sie Measuregruppen für den Cube, und klicken Sie in der Measures definieren Gruppen, die Sie Partitionen für jede Measuregruppe definieren können. Ein Nebenobjekt kann nur unter dem Hauptobjekt definiert werden, das es enthält. Weitere Informationen zu den Haupt-und nebenobjekte, finden Sie unter [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
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
 Die **ObjectExpansion** Attribut der **Alter** Befehl wurde festgelegt, um *ObjectProperties*. Mit dieser Einstellung können die [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) -Element, ein nebenobjekt aus der Datenquelle, die in definierten auszuschließende **ObjectDefinition**. Daher bleiben die Informationen zum Identitätswechsel für die Datenquelle auf "Service Account" festgelegt, wie es im ersten Beispiel angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Execute-Methode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
