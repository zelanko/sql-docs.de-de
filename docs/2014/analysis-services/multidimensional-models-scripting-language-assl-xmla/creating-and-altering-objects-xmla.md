---
title: Erstellen und Ändern von Objekten (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcc6eedc97b3d476d79420b4e067883e17f03d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702302"
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
  
 Verwenden Sie den [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) -Befehl, um ein Hauptobjekt für eine Instanz [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]von zu erstellen, und den [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) -Befehl, um ein vorhandenes Hauptobjekt in einer-Instanz zu ändern. Beide Befehle werden mit der [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methode ausgeführt.  
  
## <a name="creating-objects"></a>Erstellen von Objekten  
 Wenn Sie Objekte über die `Create`-Methode erstellen, müssen Sie zunächst das übergeordnete Objekt identifizieren, das das zu erstellende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objekt enthält. Sie identifizieren das übergeordnete Objekt, indem Sie einen Objekt Verweis in der Eigenschaft " [parametriobject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) " des `Create` Befehls angeben. Jeder Objektverweis enthält die Objektbezeichner, die notwendig sind, um das übergeordnete Objekt für den `Create`-Befehl zu identifizieren. Weitere Informationen zu Objekt verweisen finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um eine neue Measuregruppe für den Cube zu erstellen. Der Objektverweis für den Cube in der Eigenschaft `ParentObject` enthält sowohl einen Datenbankbezeichner als auch einen Cubebezeichner, da der gleiche Cubebezeichner potenziell von einer anderen Datenbank verwendet werden könnte.  
  
 Das [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) -Element enthält ASSL-Elemente (Analysis Services Scripting Language), die das zu erstellende Hauptobjekt definieren. Weitere Informationen zu ASSL finden Sie unter [entwickeln mit Analysis Services Skriptsprache &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Wenn Sie das `AllowOverwrite`-Attribut des `Create`-Befehls auf True setzen, können Sie ein vorhandenes Hauptobjekt mit dem gleichen Bezeichner überschreiben. Andernfalls tritt ein Fehler auf, wenn im übergeordneten Objekt bereits ein Hauptobjekt mit dem gleichen Bezeichner vorhanden ist.  
  
 Weitere Informationen zum- `Create` Befehl finden Sie unter [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).  
  
### <a name="creating-session-objects"></a>Erstellen von Sitzungsobjekten  
 Sitzungsobjekte sind temporäre Objekte, die nur für die explizite oder implizierte Sitzung zur Verfügung stehen, die von einer Clientanwendung verwendet werden. Bei Beendigung der Sitzung werden diese gelöscht. Sie können Sitzungs Objekte erstellen, indem Sie `Scope` das-Attribut `Create` des-Befehls auf *Session*festlegen.  
  
> [!NOTE]  
>  Wenn Sie die *Sitzungs* Einstellung verwenden, `ObjectDefinition` kann das-Element nur [Dimensions](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)-, [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)-oder [Mining Model](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) -ASSL-Elemente enthalten.  
  
## <a name="altering-objects"></a>Ändern von Objekten  
 Wenn Sie Objekte mithilfe der `Alter` -Methode ändern, müssen Sie zuerst das zu ändernde Objekt identifizieren, indem Sie einen Objekt Verweis in der [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) - `Alter` Eigenschaft des-Befehls angeben. Jeder Objektverweis enthält die Objektbezeichner, die notwendig sind, um das Objekt für den `Alter`-Befehl zu identifizieren. Weitere Informationen zu Objekt verweisen finden Sie unter [definieren und Identifizieren von Objekten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Beispielsweise müssen Sie einen Objektverweis auf einen Cube bereitstellen, um die Struktur eines Cubes zu ändern. Der Objektverweis für den Cube in der Eigenschaft `Object` enthält sowohl einen Datenbankbezeichner als auch einen Cubebezeichner, da der gleiche Cubebezeichner potenziell von einer anderen Datenbank verwendet werden könnte.  
  
 Das `ObjectDefinition`-Element enthält ASSL-Elemente, die das Hauptobjekt definieren, das geändert werden soll. Weitere Informationen zu ASSL finden Sie unter [entwickeln mit Analysis Services Skriptsprache &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Wenn Sie das `AllowCreate`-Attribut des `Alter`-Befehls auf True setzen, können Sie das angegebene Hauptobjekt erstellen, wenn das Objekt nicht existiert. Andernfalls tritt ein Fehler auf, wenn ein angegebenes Hauptobjekt nicht bereits vorhanden ist.  
  
### <a name="using-the-objectexpansion-attribute"></a>Verwenden des ObjectExpansion-Attributs  
 Wenn Sie nur die Eigenschaften des Haupt Objekts ändern und keine Hilfsobjekte neu definieren, die im Hauptobjekt enthalten sind, können Sie das `ObjectExpansion` -Attribut des- `Alter` Befehls auf *ObjectProperties*festlegen. Die `ObjectDefinition`-Eigenschaft muss dann nur die Elemente für die Eigenschaften des Hauptobjekts enthalten, und der `Alter`-Befehl lässt die zum Hauptobjekt gehörenden Nebenobjekte unverändert.  
  
 Zum Neudefinieren von neben Objekten für ein Hauptobjekt müssen Sie das `ObjectExpansion` -Attribut auf *ExpandFull* festlegen, und die Objektdefinition muss alle neben Objekte enthalten, die im Hauptobjekt enthalten sind. Wenn die `ObjectDefinition`-Eigenschaft des `Alter`-Befehls nicht explizit ein im Hauptobjekt enthaltenes Nebenobjekt einbindet, wird das nicht eingebundene Nebenobjekt gelöscht.  
  
### <a name="altering-session-objects"></a>Ändern von Sitzungsobjekten  
 `Create` Um die vom Befehl erstellten Sitzungs Objekte zu ändern, legen `Scope` Sie das- `Alter` Attribut des-Befehls auf *Session*fest.  
  
> [!NOTE]  
>  Wenn Sie die *Sitzungs* Einstellung verwenden, `ObjectDefinition` kann das-Element nur [Dimensions](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)-, [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)-oder [Mining Model](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) -ASSL-Elemente enthalten.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Erstellen oder Ändern von untergeordneten Objekten  
 Obwohl ein `Create`- oder  `Alter`-Befehl nur das oberste Hauptobjekt erstellt oder ändert, kann das Hauptobjekt, das erstellt oder geändert wird, Definitionen innerhalb der einschließenden `ObjectDefinition`-Eigenschaft für andere Haupt- und Nebenobjekte enthalten, die ihm untergeordnet sind. Beispielsweise geben Sie bei der Definition eines Cubes die übergeordnete Datenbank in `ParentObject` an, und innerhalb der Cubedefinition in `ObjectDefinition` können Sie Measuregruppen für den Cube erstellen, und innerhalb der Measuregruppen können Sie Partitionen für jede Measuregruppe definieren. Ein Nebenobjekt kann nur unter dem Hauptobjekt definiert werden, das es enthält. Weitere Informationen zu Haupt-und neben Objekten finden Sie unter [Datenbankobjekte &#40;Analysis Services-Mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel wird eine relationale Datenquelle erstellt, [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf die-Beispieldatenbank verweist.  
  
### <a name="code"></a>Code  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
### <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel wird die im vorherigen Beispiel erzeugte relationale Datenquelle so geändert, dass der Abfragetimeout der Datenquelle nach 30 Sekunden einsetzt.  
  
### <a name="code"></a>Code  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
 Das `ObjectExpansion` -Attribut des `Alter` -Befehls wurde auf *ObjectProperties*festgelegt. Diese Einstellung ermöglicht es, dass das Element "Identitätswechsel [Informationen](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) " (ein neben Objekt) aus der in `ObjectDefinition`definierten Datenquelle ausgeschlossen wird. Daher bleiben die Informationen zum Identitätswechsel für die Datenquelle auf "Service Account" festgelegt, wie es im ersten Beispiel angegeben ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Execute-Methode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Entwickeln mit Analysis Services Skriptsprache &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
