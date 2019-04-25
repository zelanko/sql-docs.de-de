---
title: CSDLBI-Konzepte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bf73822e8872397499bdfbc04bab6747035fbec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757947"
---
# <a name="csdlbi-concepts"></a>CSDLBI-Konzepte
  Die konzeptionelle Schemadefinitionssprache mit BI-Anmerkungen (CSDLBI) basiert auf Entity Data Framework, einer Abstraktion zum Darstellen von Daten, die es ermöglicht, dass unterschiedliche Datasets programmgesteuert aufgerufen, abgefragt oder exportiert werden können. CSDLBI wird verwendet, um mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellte Datenmodelle darzustellen, weil diese Sprache umfangreiche datengesteuerte Berichterstellungsfunktionen und Anwendungen unterstützt.  
  
 In diesem Abschnitt wird erläutert, wie die CSDLBI-Darstellung (tabellarischen und mehrdimensionalen) [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenmodellen zugeordnet wird, und es werden Beispiele für die einzelnen Modelltypen bereitgestellt.  
  
 Die Beispiele zur Veranschaulichung dieser Konzepte wurden aus der Beispieldatenbank AdventureWorks, verfügbar auf CodePlex, entnommen. Weitere Informationen zu den Beispielen finden Sie unter [Adventure Works-Beispiele für SQL Server](https://go.microsoft.com/fwlink/?linkID=220093).  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a>Struktur eines tabellarischen Modells in CSDLBI  
 Ein CSDLBI-Dokument, in dem ein Berichtsmodell und seine Daten beschrieben werden, beginnt mit der xsd-Anweisung, gefolgt von der Definition eines Modells.  
  
 Das Modell ist ein Namespace, der die folgenden Hauptentitäten, Zuordnungen und Eigenschaften enthält:  
  
-   Der `EntityContainer` listet die Tabellen im Modell auf.  
  
-   Jede Tabelle wird mit dem `EntityContainer` als `EntitySet` aufgeführt.  
  
-   Jede Beziehung zwischen zwei Tabellen wird als `AssociationSet` beschrieben, der die Beziehungsendpunkte und die Beziehungsrollen definiert.  
  
-   Das `EntityType`-Element wird erweitert, damit BISM weitere Details zu den Tabellen und den darin enthaltenen Spalten bereitstellt, einschließlich Eigenschaften zu Sortierungs- und Anzeigezwecken.  
  
-   Das `Measure`-Element definiert Berechnungen, die im Modell verwendet werden können. Ein Measure kann in einen KPI umgewandelt werden, indem mithilfe des neuen `KPI`-Elements ein Satz besonderer Anzeigeattribute hinzugefügt wird.  
  
-   Es gibt keine separate Darstellung von Perspektiven. Spalten und Tabellen, die nicht in einer Perspektive enthalten, sind in der CSDL vorhanden, aber sind mit dem `Hidden`-Attribut gekennzeichnet.  
  
### <a name="entities-entitysets-and-entitytypes"></a>Entitäten, EntitySets und EntityTypes  
 Die Idee einer Entität in Entity Data Framework wird erweitert, um Spalten und Tabellen aus dem Datenmodell darzustellen. Der folgende Auszug zeigt die Liste der `EntitySet`-Elemente in einem einfachen Modell, das nur drei Tabellen enthält.  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 `EntitySet` enthält keine Informationen zu Spalten oder Daten in der Tabelle. Die ausführliche Beschreibung der Spalten und ihrer Eigenschaften wird im EntityType-Element bereitgestellt.  
  
 Das `EntitySet`-Element für jede Entität (Tabelle) umfasst eine Auflistung von Eigenschaften, die die Schlüsselspalte, den Datentyp und die Länge der Spalte, die NULL-Zulässigkeit, das Sortierverhalten usw. definieren. Im folgenden CSDL-Auszug werden z. B. drei Spalten in der Customer-Tabelle beschrieben. Die erste Spalte ist eine spezielle ausgeblendete Spalte, die intern vom Modell verwendet wird.  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 Um die Größe des generierten CSDLBI-Dokuments einzuschränken, werden Eigenschaften, die mehr als einmal in einer Entität vorkommen, durch einen Verweis auf eine vorhandene Eigenschaft angegeben, damit die Eigenschaft für `EntityType` nur einmal aufgeführt werden muss. Die Clientanwendung kann den Wert der Eigenschaft abrufen, indem sie den `EntityType` sucht, der dem `OriginEntityType` entspricht.  
  
### <a name="relationships"></a>Beziehungen  
 Beziehungen werden im Entity Data Framework, wie definiert *Zuordnungen* zwischen Entitäten.  
  
 Zuordnungen haben immer genau zwei Enden, die jeweils auf ein Feld oder eine Spalte in einer Tabelle zeigen. Daher sind mehrere Beziehungen zwischen zwei Tabellen möglich, wenn die Beziehungen verschiedene Endpunkte haben. Den Endpunkten der Zuordnung wird ein Rollenname zugewiesen, der angibt, wie die Zuordnung im Kontext des Datenmodells verwendet wird. Ein Beispiel für einen Rollennamen ein möglicherweise **"ShipTo"**, wenn auf eine Kunden-ID angewendet wird, die die Kunden-ID in der Tabelle Orders zugeordnet ist.  
  
 Die CSDLBI-Darstellung des Modells enthält auch Attribute in der Zuordnung, die bestimmen, wie die Entitäten einander in Hinsicht zugeordnet werden die *Multiplizität* der Zuordnung. Multiplizität gibt an, ob das Attribut oder die Spalte am Endpunkt einer Beziehung zwischen Tabellen auf der 1-Seite oder auf der n-Seite einer 1:n-Beziehung ist. Es gibt keinen separaten Wert für 1:1-Beziehungen. CSDLBI-Anmerkungen unterstützen eine Multiplizität von 0 (das bedeutet, dass die Entität nicht zugeordnet ist) oder 0..1, was entweder eine 1:1-Beziehung oder eine 1:n-Beziehung bedeutet.  
  
 Im folgenden Beispiel wird die CSDLBI-Ausgabe für eine Beziehung zwischen den Tabellen "Date" und "ProductInventory" dargestellt, wobei die zwei Tabellen über die DateAlternateKey-Spalte verknüpft sind. Standardmäßig ist der Name von `AssociationSet` der vollqualifizierte Name der Spalten, die an der Beziehung beteiligt sind. Sie können dieses Verhalten jedoch ändern, wenn Sie das Modell erstellen, und ein anderes Namensformat verwenden.  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a>Visualisierungs- und Navigationseigenschaften  
 Ein wichtiger Teil der CSDLBI-Anmerkungen sind die Eigenschaften zum Definieren der Darstellung auf der Berichtsebene sowie zum Navigieren in den Beziehungen zwischen Entitäten. Wenn Sie ein Datenmodell erstellen, sehen Sie es in der Regel nicht als wichtig an, die Sortierung oder Gruppierung der Daten zu steuern oder einen Standardwert anzugeben, in der Annahme, dass die Clientanwendung die Reihenfolge und andere Details der Darstellung angibt. Tabellarische [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Modelle werden jedoch für die Integration in den [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]-Berichtserstellungsclient entworfen und schließen Eigenschaften ein, die die Darstellung der Entitäten aus dem Datenmodell auf der Berichtsentwurfsoberfläche unterstützen.  
  
 Erweiterungen für Visualisierung umfassen Attribute zum Angeben der Standardaggregation, die mit numerischen Daten verwendet werden soll, zum Angeben, dass ein Textfeld auf eine URL eines Bilds zeigt, oder zum Angeben des Felds, das verwendet wurde, um das aktuelle Feld zu sortieren.  
  
### <a name="name-properties-and-naming-conventions"></a>Namenseigenschaften und Namenskonventionen  
 Das CSDLBI-Schema setzt voraus, dass jede Entität über einen eindeutigen Namen und einen Bezeichner verfügt, die als Schlüssel verwendet werden können. Außerdem können einige Entitäten über zu Anzeigezwecken verwendete Beschriftungen und Kontextnamen verfügen, die sich abhängig davon ändern, wo die Entität verwendet wird.  
  
 Das `Documentation`-Element bietet Berichts-Designern die Möglichkeit, eine Beschreibung der Entität bereitzustellen, um Geschäftsanwendern die Bedeutung der Daten zu vermitteln. Einige Entitäten unterstützen auch eines oder mehrere `Annotation`-Attribute, die zusätzliche Metadaten für die Anwendung oder Clients bereitstellen.  
  
 Wenn Sie mit den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Tools ein Modell generieren, folgen die Namen, die für Objekte erstellt werden, den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Konventionen für Objektbenennung und Namenseindeutigkeit. Da jedoch CSDLBI auf dem Entity Data Framework (EDF) basiert, welches erfordert, dass Namen die Konventionen für C#-Bezeichner einhalten, nimmt der Server, wenn er die CSDLBI-Ausgabe für ein Modell erstellt, die innerhalb des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Schemas verwendeten Namen und erstellt automatisch neue Objektnamen, die den EDF-Anforderungen entsprechen. In der folgenden Tabelle werden die Vorgänge, durch die die neuen Namen generiert werden, beschrieben.  
  
|Rule|Aktion|  
|----------|------------|  
|Keine unzulässigen Zeichen|Unzulässige Zeichen werden durch Unterstriche ersetzt.|  
|Namen müssen eindeutig sein|Wenn zwei Zeichenfolgen gleich sind, wird an eine ein Unterstrich plus eine Zahl angefügt, um sie eindeutig zu machen|  
  
> [!WARNING]  
>  Beschriftungen und Qualifizierer haben beide Übersetzungen, und für eine bestimmte Sprache kann das eine oder das andere vorhanden sein. Das bedeutet, dass in Fällen, wo ein Qualifizierer und ein Name oder ein Qualifizierer und eine Beschriftung verkettet sind, die Zeichenfolgen in zwei verschiedenen Sprachen vorliegen können.  
  
## <a name="additions-to-support-multidimensional-models"></a>Ergänzungen zur Unterstützung mehrdimensionaler Modelle  
 In Version 1.0 der CSDLBI-Anmerkungen wurden nur tabellarische Modelle unterstützt. Version 1.1. wurde durch die Unterstützung mehrdimensionaler Modelle (OLAP-Cubes) erweitert, die mithilfe herkömmlicher BI-Entwicklungstools erstellt wurden. Daher können nun zur Berichterstellung XML-Anforderungen für ein mehrdimensionales Modell ausgeben werden und eine CSDLBI-Definition des Modells kann empfangen werden.  
  
 **Cubes:** Eine SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabellarische Datenbank kann nur einen Modus umfassen. Im Gegensatz dazu kann jede mehrdimensionale Datenbank mehrere Cubes enthalten, wobei jede Datenbank einem Standardcube zugeordnet ist. Wenn Sie eine XML-Anforderung für einen mehrdimensionalen Server ausgeben, muss daher der Cube angegeben werden; andernfalls wird das XML für den Standardcube zurückgegeben.  
  
 Die Darstellung eines Cubes ähnelt ansonsten sehr stark der einer tabellarischen Modelldatenbank. Der Cubename und der Cube entsprechen dem Namen und dem Bezeichner der tabellarischen Datenbank.  
  
 **Dimensionen:** Eine Dimension wird in CSDLBI als Entität (Tabelle) mit Spalten und Eigenschaften dargestellt. Beachten Sie, dass eine Dimension im Modell, auch wenn sie nicht in einer Perspektive enthalten ist, in der CSDL-Ausgabe zwar dargestellt wird, jedoch als `Hidden` gekennzeichnet ist.  
  
 **Perspektiven:** Ein Client kann CSDL für einzelne Perspektiven anfordern. Weitere Informationen finden Sie unter [DISCOVER_CSDL_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).  
  
 **Hierarchien:** Hierarchien werden unterstützt und wird in CSDLBI als Satz von Ebenen dargestellt.  
  
 **Mitglieder:** Unterstützung für das Standardelement wurde hinzugefügt, und Standardwerten werden die CSDLBI-Ausgabe automatisch hinzugefügt.  
  
 **Berechnete Elemente:** Mehrdimensionale Modelle unterstützen berechnete Elemente für untergeordnetes Element des **alle** mit einem einzelnen realen Element.  
  
 **Dimensionsattribute:** Dimensionsattribute werden in CSDLBI-Ausgabe unterstützt und automatisch als nicht aggregierbar gekennzeichnet.  
  
 **KPIs:** KPIs wurden in CSDLBI, Version 1.1 unterstützt, aber die Darstellung geändert hat. Bisher war ein KPI eine Eigenschaft eines Measures. In Version 1.1 kann das KPI-Element einem Measure hinzugefügt werden.  
  
 **Neue Eigenschaften:** Zusätzliche Attribute wurden hinzugefügt, um DirectQuery-Modelle zu unterstützen.  
  
 **Einschränkungen:** Zellensicherheit wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [CSDL-Anmerkungen für Business Intelligence &#40;CSDLBI&#41;](https://docs.microsoft.com/bi-reference/csdl/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
