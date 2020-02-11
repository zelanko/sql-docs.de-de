---
title: Syntax für Elementpfade für XML-Berichtsdaten (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9981a3ebeb1b67bda67509e2a08995fadb195abb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107300"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a>Syntax für Elementpfade für XML-Berichtsdaten (SSRS)
  Im Berichts-Designer geben Sie die Daten, die für einen Bericht aus einer XML-Datenquelle verwendet werden sollen, durch Definieren eines Elementpfades (mit Unterscheidung von Groß-/Kleinschreibung) an. Mit einem Elementpfad wird angegeben, wie die hierarchischen XML-Knoten und ihre Attribute in der XML-Datenquelle durchsucht werden können. Lassen Sie die Datasetabfrage oder den XML-`ElementPath` der XML-`Query` leer, um den Standardelementpfad zu verwenden. Wenn Daten aus der XML-Datenquelle abgerufen werden, werden Elementknoten mit Textwerten und Elementknotenattribute im Resultset zu Spalten. Die Werte der Knoten und Attribute werden beim Ausführen der Abfrage zu Zeilendaten. Die Spalten werden als Datasetfeldauflistung im Berichtsdatenbereich angezeigt. In diesem Thema wird die Syntax für Elementpfade beschrieben.  
  
> [!NOTE]  
>  Die Syntax von Elementpfaden ist nicht vom Namespace abhängig. Um Namespaces in einem Element Pfad zu verwenden, verwenden Sie die XML-Abfrage Syntax, `ElementPath` die ein XML-Element enthält, das in [XML Query-Syntax für XML-Berichtsdaten &#40;SSRS-&#41;](report-data-ssrs.md)beschrieben wird.  
  
 In der folgenden Tabelle werden Konventionen für das Definieren eines Elementpfades beschrieben.  
  
|Konvention|Syntaxelemente|  
|----------------|--------------|  
|**Fett**|Text, der genau so geschrieben werden muss wie dargestellt.|  
|&#124; (senkrechter Strich)|Trennt Syntaxelemente voneinander. Sie können nur eines der Elemente auswählen.|  
|`[ ] (brackets)`|Optionale Syntaxelemente. Geben Sie die eckigen Klammern nicht mit ein.|  
|**{ }** (geschweifte Klammern)|Begrenzt Parameter für Syntaxelemente.|  
|[ **,** ...*n*]|Zeigt an, dass das vorherige Element *n* -mal wiederholt werden kann. Die einzelnen Vorkommen werden durch Kommas getrennt.|  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle sind Begriffe für Pfadelemente zusammengefasst. Die Beispiele in der Tabelle beziehen sich auf das XML-Beispieldokument Customers.xml, das im Abschnitt mit Beispielen in diesem Thema enthalten ist.  
  
> [!NOTE]  
>  Bei XML-Tags wird zwischen Groß- und Kleinschreibung unterschieden. Wenn Sie im Elementpfad einen Elementknoten (ElementNode) angeben, müssen die XML-Tags in der Datenquelle genau übereinstimmen.  
  
|Begriff|Definition|  
|----------|----------------|  
|Elementpfad|Definiert die zu durchsuchende Sequenz von Knoten im XML-Dokument, um Felddaten für ein Dataset mit einer XML-Datenquelle abzurufen.|  
|`ElementNode`|Der XML-Knoten im XML-Dokument. Knoten werden durch Tags gekennzeichnet und sind in einer hierarchischen Beziehung mit anderen Knoten vorhanden. Bei <Kunden\< handelt es sich beispielsweise um den Stammknoten des Elements. <Kunde\< ist ein untergeordnetes Element von <Kunden\<.|  
|`XMLName`|Der Name des Knotens. Der Name des Knotens Customers ist beispielsweise Customers. Für `XMLName` kann ein Namespacebezeichner als Präfix verwendet werden, um jeden Knoten eindeutig zu benennen.|  
|`Encoding`|Gibt an, dass der `Value` für dieses Element codiertes XML darstellt und decodiert werden sowie als untergeordnetes Element dieses Elements aufgenommen muss.|  
|`FieldList`|Definiert eine Gruppe von Elementen und Attributen, die zum Abrufen von Daten verwendet werden.<br /><br /> Wenn dieses Element nicht angegeben wird, werden alle Attribute und untergeordneten Elemente als Felder verwendet. Wenn die leere Feldliste angegeben wird ( **{}** ), werden keine Felder von diesem Knoten verwendet.<br /><br /> Eine `FieldList` kann nicht gleichzeitig einen `Value` und ein `Element` oder einen `ElementNode` enthalten.|  
|`Field`|Gibt die Daten an, die als Datasetfeld abgerufen werden.|  
|`Attribute`|Ein Name/Wert-Paar im `ElementNode`. \<Beispielsweise `ID` ist im Elementknoten Customer ID = "1" > ein Attribut und `@ID(Integer)` gibt "1" als ganzzahligen Typ im entsprechenden Datenfeld `ID`zurück.|  
|`Value`|Der Wert des Elements. 
  `Value` kann nur für den letzten `ElementNode` im Elementpfad verwendet werden. Da \<z. b. Return> ein Blattknoten ist, wenn Sie ihn am Ende eines Element Pfads einschließen, ist `Return {@}` `Chair`der Wert von.|  
|`Element`|Der Wert des benannten untergeordneten Elements. Beispielsweise werden mithilfe von Customers {}/Customer {}/LastName nur Werte für das LastName-Element abgerufen.|  
|`Type`|Der optionale Datentyp, der für das aus diesem Element erstellte Feld zu verwenden ist.|  
|`NamespacePrefix`|
  `NamespacePrefix` wird im XML-Abfrageelement definiert. Wenn kein XML-Abfrageelement vorhanden ist, werden Namespaces im XML-`ElementPath` ignoriert. Wenn ein XML-Abfrageelement vorhanden ist, verfügt der XML-`ElementPath` über das optionale Attribut `IgnoreNamespaces`. Wenn IgnoreNamespaces ist `true`, werden Namespaces im XML `ElementPath` -und XML-Dokument ignoriert. Weitere Informationen finden Sie unter [XML-Abfragesyntax für XML-Berichtsdaten (SSRS)](report-data-ssrs.md).|  
  
## <a name="example---no-namespaces"></a>Beispiel – Keine Namespaces  
 In den folgenden Beispiele wird das XML-Dokument "Customers.xml" verwendet. Diese Tabelle zeigt Beispiele zur Syntax von Elementpfaden und die Ergebnisse beim Verwenden des Elementpfades in einer Abfrage an, die ein Dataset anhand eines als Datenquelle dienenden XML-Dokuments definiert.  
  
 Beachten Sie Folgendes: Wenn der Element Pfad leer ist, wird in der Abfrage der Standardelement Pfad verwendet: der erste Pfad zu einer Blattknoten Auflistung. Im ersten Beispiel entspricht das Leerlassen des Elementpfades dem Angeben des Elementpfades /Customers/Customer/Orders/Order. Alle Knotenwerte und -attribute entlang dieses Pfades werden im Resultset zurückgegeben, und die Knotennamen und -attribute werden als Datasetfelder angezeigt.  
  
-   *Leer*  
  
    |Order|Qty (Menge)|id|FirstName|LastName|Customer.ID|xmlns|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |Chair|6|1|Bobby|Moore|11|http://www.adventure-works.com|  
    |Tabelle|1|2|Bobby|Moore|11|http://www.adventure-works.com|  
    |Sofa|2|8|Crystal|Hu|20|http://www.adventure-works.com|  
    |EndTables|2|15|Wyatt|Diaz|33|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |FirstName|LastName|id|  
    |---------------|--------------|--------|  
    |Bobby|Moore|11|  
    |Crystal|Hu|20|  
    |Wyatt|Diaz|33|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |LastName|  
    |--------------|  
    |Moore|  
    |Hu|  
    |Diaz|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |Order|Qty (Menge)|  
    |-----------|---------|  
    |Chair|6|  
    |Tabelle|1|  
    |Sofa|2|  
    |EndTables|2|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |Order.ID|FirstName|LastName|id|  
    |--------------|---------------|--------------|--------|  
    |1|Bobby|Moore|11|  
    |2|Bobby|Moore|11|  
    |8|Crystal|Hu|20|  
    |15|Wyatt|Diaz|33|  
  
#### <a name="xml-document-customersxml"></a>XML-Dokument: Customers.xml  
 Um die Elementpfadbeispiele im vorherigen Abschnitt auszuprobieren, können Sie dieses XML-Dokument kopieren und unter einer URL speichern, auf die der Berichts-Designer zugreifen kann. Anschließend können Sie das XML-Dokument als XML-Datenquelle verwenden: z. B. `http://localhost/Customers.xml`  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 Sie können auch eine XML-Datenquelle ohne Verbindungszeichenfolge erstellen und Customers.XML in die Abfrage einbetten. Gehen Sie dazu wie folgt vor:  
  
###### <a name="to-embed-customersxml-in-a-query"></a>So betten Sie Customers.XML in einer Abfrage ein  
  
1.  Erstellen Sie eine XML-Datenquelle mit einer leeren Verbindungszeichenfolge.  
  
2.  Erstellen Sie ein neues Dataset für die XML-Datenquelle.  
  
3.  Klicken Sie im Dialogfeld **Dataseteigenschaften** auf **Abfrage-Designer**. Das textbasierte Dialogfeld des Abfrage-Designers wird geöffnet.  
  
4.  Geben Sie die folgenden Zeilen im Abfragebereich ein:  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  Kopieren Sie die Datei Customers.XML, und fügen Sie den Text im Abfragebereich nach der Zeile `<XmlData>`ein.  
  
6.  Löschen Sie im Abfragebereich die erste Zeile, die Sie aus der Datei Customers.XML kopiert haben: `<?xml version="1.0"?>`  
  
7.  Fügen Sie am Ende der Abfrage die beiden folgenden Zeilen hinzu:  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  Klicken Sie auf **Abfrage ausführen** (!).  
  
     Das Resultset zeigt vier Datenzeilen mit den folgenden Spalten an: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Verbindungstyp &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Reporting Services-Tutorials (SSRS)](../reporting-services-tutorials-ssrs.md)   
 [Hinzufügen, Bearbeiten und Aktualisieren von Feldern im Berichtsdatenbereich &#40;Berichts-Generator und SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
