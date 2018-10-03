---
title: XML-Abfragesyntax für XML-Berichtsdaten (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 65eed443f671f18944ce381a011498e3ca23af4e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102890"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a>XML-Abfragesyntax für XML-Berichtsdaten (SSRS)
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]können Sie Datasets für XML-Datenquellen erstellen. Wenn Sie eine Datenquelle definiert haben, erstellen Sie eine Abfrage für das Dataset. Je nach Art der XML-Daten, die auf die Datenquelle zeigt, Sie die Datasetabfrage erstellen, indem XML einschließlich `Query` oder einen Elementpfad. XML `Query` beginnt mit einem  **\<Abfrage >** -Tag und enthält Namespaces und XML-Elemente, die je nach Datenquelle variieren. Ein Elementpfad ist von Namespaces unabhängig und gibt die Knoten und Knotenattribute in den zugrunde liegenden XML-Daten an, die mit der XPath-ähnlichen Syntax verwendet werden sollen. Weitere Informationen zu Elementpfaden finden Sie unter [Syntax für Elementpfade für XML-Berichtsdaten (SSRS)](report-data-ssrs.md).  
  
 Sie können eine XML-Datenquelle für die folgenden Typen von XML-Daten erstellen:  
  
-   XML-Dokumente, auf die eine URL über HTTP zeigt  
  
-   Webdienst-Endpunkte, die XML-Daten zurückgeben  
  
-   Eingebettete XML-Daten  
  
 Die Art, wie Sie eine XML-`Query` oder einen Elementpfad angeben, ist vom Typ der XML-Daten abhängig.  
  
 Ein XML-Dokument, das XML- `Query` ist optional. Wenn sie eingeschlossen wird, kann sie einen optionalen XML-`ElementPath` enthalten. Der Wert des XML-`ElementPath` verwendet die Syntax des Elementpfades. Sie schließen die XML- `Query` und XML- `ElementPath` um Namespaces ordnungsgemäß zu verarbeiten, wenn er von der XML-Daten aus der Datenquelle benötigt wird.  
  
 Für einen Webdienst-Endpunkt, auf den eine Verbindungszeichenfolgen-URL zeigt, definiert die XML-`Query` die Webdienstmethode, die SOAP-Aktion oder beide. Der XML-Datenanbieter erstellt eine Webdienstanforderung, mit der XML-Daten abgerufen werden, die im Bericht verwendet werden sollen.  
  
> [!NOTE]  
>  Wenn ein Webdienst-Namespace ein Schrägstrichzeichen (`/)` enthält, fügen Sie die Webdienstmethode und die SOAP-Aktion ein, sodass die XML-Datenverarbeitungserweiterung den Namespace fehlerfrei ableiten kann.  
  
 Für ein eingebettetes XML-Dokument, das XML- `Query` definiert den zu verwendenden eingebetteten XML-Daten, enthält Sie optionale Namespaces und einen optionalen XML- `ElementPath`...  
  
## <a name="specifying-query-parameters-for-xml-data"></a>Angeben von Abfrageparametern für XML-Daten  
 Sie können Abfrageparameter für XML-Dokumente angeben.  
  
-   Bei URL-Anforderungen sind die Abfrageparameter als URL-Standardparameter enthalten.  
  
-   Bei Webdienstanforderungen werden Abfrageparameter an die Webdienstmethode übergeben. Verwenden Sie zum Definieren eines Abfrageparameters im Dialogfeld **Dataseteigenschaften** die Seite **Parameter** . Weitere Informationen finden Sie unter [Dataset Properties Dialog Box, Parameter](dataset-properties-dialog-box-parameters.md).  
  
### <a name="example"></a>Beispiel  
 Die Beispiele in der folgenden Tabelle veranschaulichen das Abrufen von Daten vom Berichtsserver-Webdienst, einem XML-Dokument und eingebetteten XML-Daten.  
  
|XML-Datenquelle|Abfragebeispiel|  
|---------------------|-------------------|  
|XML-Webdienstdaten ListChildren-Methode.|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="http://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|Webdienst-XML-Daten von SoapAction.|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|XML-Dokument oder eingebettete XML-Daten, die Namespaces verwenden.<br /><br /> Abfrageelement, das Namespaces für einen Elementpfad angibt.|`<Query xmlns:es="http://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|Eingebettetes XML-Dokument.|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|XML-Dokument, das Standardwerte verwendet.|*No query*.<br /><br /> Der Elementpfad wird vom XML-Dokument selbst abgeleitet und ist von Namespaces unabhängig.|  
  
> [!NOTE]  
>  Im ersten Webdienstbeispiel wird der Inhalt des Berichtsservers aufgeführt, der die <xref:ReportService2006.ReportingService2006.ListChildren%2A> -Methode Diese Abfrage können Sie ausführen, indem Sie eine neue Datenquelle erstellen und die Verbindungszeichenfolge auf http://localhost/reportserver/reportservice2006.asmx festlegen. Die <xref:ReportService2006.ReportingService2006.ListChildren%2A> Methode akzeptiert zwei Parameter: `Item` und `Recursive`. Legen Sie den Standardwert für `Item` zu `/` und `Recursive` zu `1`.  
  
## <a name="specifying-namespaces"></a>Angeben von Namespaces  
 Verwenden Sie das XML `Query` -Element zum Angeben von Namespaces, die verwendet werden, in die XML-Daten aus der Datenquelle. In der folgenden XML-Abfrage wird der Namespace `sales` verwendet. Die XML-`ElementPath`-Knoten für `sales:LineItems` und `sales:LineItem` verwenden den Namespace `sales`.  
  
```  
<Query xmlns:sales=  
"http://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      http://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 Verwenden Sie zum Namespace des Datenanbieters angeben, damit der Standardnamespace leer bleibt `xmldp`. Dies wird im folgenden Beispiel gezeigt.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das XML-Dokument DPNamespace.xml verwendet, das zur Veranschaulichung unter der Tabelle bereitgestellt ist. In dieser Tabelle sind zwei Beispiele für XML-ElementPath-Syntax angegeben, die Namespacepräfixe enthalten.  
  
|XML-Abfrageelement|Resultierende Felder im Dataset|  
|-----------------------|-------------------------------------|  
|\<Query/>|Wert A: http://schemas.microsoft.com/...<br /><br /> Wert B: http://schemas.microsoft.com/...<br /><br /> Wert C: http://schemas.microsoft.com/...|  
|\<XmlDP:Query Xmlns:xmldp = "http://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" Xmlns:ns = "http://schemas.microsoft.com/..." ><br /><br /> \<XmlDP:ElementPath > Stamm {}/ns:Element2 / Knoten\</xmldp:ElementPath ><br /><br /> \</XmlDP:Query >|Value D<br /><br /> Value E<br /><br /> Value F|  
  
#### <a name="xml-document-dpnamespacexml"></a>XML-Dokument: DPNamespace.xml  
 Sie können dieses XML-Dokument kopieren und unter einer URL speichern, auf den der Berichts-Designer zugreifen kann, um es als XML-Datenquelle zu verwenden: z. B. http://localhost/DPNamespace.xml.  
  
```  
<Root xmlns:ns="http://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Verbindungstyp &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
