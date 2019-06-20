---
title: Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10421"
ms.assetid: 7e103637-4371-43d7-821c-d269c2cc1b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eb8d81c9c47f00ed84036accf86768d084072c4d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109491"
---
# <a name="data-connections-data-sources-and-connection-strings-in-report-builder"></a>Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator
  Um Daten in einen Bericht einzuschließen, erstellen Sie Datenverbindungen und Datasets. Eine Datenverbindung schließt Informationen zum Zugreifen auf eine externe Datenquelle ein. Ein Dataset enthält einen Abfragebefehl, der angibt, welche Daten mit der Datenverbindung eingeschlossen werden sollen.  
  
1.  **Datenquellen im Berichtsdatenbereich:** Eine Datenquelle wird im Berichtsdatenbereich angezeigt, nachdem Sie eine eingebettete Datenquelle erstellt oder eine freigegebene Datenquelle hinzugefügt haben.  
  
2.  **Dialogfeld „Verbindung“:** Verwenden Sie das Dialogfeld „Verbindung“, um eine Verbindungszeichenfolge zu erstellen oder eine Verbindungszeichenfolge einzufügen.  
  
3.  **Datenverbindungsinformationen:** Die Verbindungszeichenfolge wird an die Datenerweiterung übergeben.  
  
4.  **Anmeldeinformationen:** Anmeldeinformationen werden getrennt von der Verbindungszeichenfolge verwaltet.  
  
5.  **Datenerweiterung/Datenanbieter:** Die Verbindung mit den Daten kann über mehrere Datenzugriffsebenen hergestellt werden.  
  
6.  **Externe Datenquellen:** Rufen Sie Daten aus relationalen Datenbanken, mehrdimensionalen Datenbanken, SharePoint-Listen, Webdiensten oder Berichtsmodellen ab.  
  
 Weitere Informationen finden Sie unter [eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41; ](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) und [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Daten können auch mithilfe von vordefinierten freigegebenen Datenquellen, freigegebenen Datasets und Berichtsteilen in einen Bericht eingeschlossen werden. Diese Elemente verfügen bereits über die erforderlichen Informationen zur Datenverbindung. Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 ![Reporting Services_Datenquellenverlauf](media/rs-datasourcesstory.gif "Rs_DataSourcesStory")  
  
##  <a name="ConnectionString"></a> Beispiele für Verbindungszeichenfolgen  
 Eine Datenverbindung enthält eine Verbindungszeichenfolge, die in der Regel vom Besitzer der externen Datenquelle bereitgestellt wird. In der folgenden Tabelle sind Beispiele von Verbindungszeichenfolgen für verschiedene externe Datenquellentypen aufgeführt.  
  
|**Datenquelle**|**Beispiel**|**Beschreibung**|  
|---------------------|-----------------|---------------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank auf dem lokalen Server|`data source="(local)";initial catalog=AdventureWorks2012`|Legen Sie den Datenquellentyp auf `SQL Server` fest.|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzdatenbank|`Data Source=localhost\MSSQL12.InstanceName; Initial Catalog= AdventureWorks2012`|Legen Sie den Datenquellentyp auf `SQL Server` fest.|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express-Datenbank|`Data Source=localhost\MSSQL12.SQLEXPRESS; Initial Catalog= AdventureWorks2012`|Legen Sie den Datenquellentyp auf `SQL Server` fest.|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank auf dem lokalen Server|`data source=localhost;initial catalog=Adventure Works DW 2012`|Legen Sie den Datenquellentyp auf `SQL Server Analysis Services` fest.|  
|SharePoint-Liste|`data source=http://MySharePointWeb/MySharePointSite/`|Legen Sie den Datenquellentyp auf `SharePoint List` fest.|  
||||  
|Berichtsmodelle|Nicht verfügbar.|Sie benötigen keine Verbindungszeichenfolge für ein Berichtsmodell. Wechseln Sie im Berichts-Generator zum Berichtsserver, und wählen Sie die SMDL-Datei aus, die das Berichtsmodell darstellt.|  
|Oracle-Server|`data source=myserver`|Legen Sie den Datenquellentyp auf `Oracle` fest. Auf dem Computer mit dem Berichts-Generator und auf dem Berichtsserver müssen die Oracle-Clienttools installiert sein.|  
|SAP NetWeaver BI-Datenquelle|`DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Legen Sie den Datenquellentyp auf `SAP NetWeaver BI` fest.|  
|Hyperion Essbase-Datenquelle|`Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Legen Sie den Datenquellentyp auf `Hyperion Essbase` fest.|  
|Teradata-Datenquelle|`data source=` *\<NN>.\<NNN>.\<NNN>.\<N>* `;`|Legen Sie den Datenquellentyp auf `Teradata` fest. Die Verbindungszeichenfolge ist eine IP-Adresse (Internet Protocol) in Form von vier Feldern, wobei jedes Feld ein bis drei Ziffern aufweisen kann.|  
|Teradata-Datenquelle|`Database=` *\<Databankname>* `; data source=` *\<NN*N *>.\<NNN>.\<NNN>.\<N*NN*>*`;Use X Views=False;Restrict to Default Database=True`|Legen Sie den Datenquellentyp auf `Teradata` fest, ähnlich dem vorherigen Beispiel. Verwenden Sie nur die Standarddatenbank, die im Datenbank-Tag angegeben wird, und ermitteln Sie nicht automatisch Datenbeziehungen.|  
|XML-Datenquelle, Webdienst|`data source=http://adventure-works.com/results.aspx`|Legen Sie den Datenquellentyp auf `XML` fest. Die Verbindungszeichenfolge ist eine URL für einen Webdienst, der Webdienste-Definitionssprache (WSDL) unterstützt.|  
|XML-Datenquelle, XML-Dokument|`http://localhost/XML/Customers.xml`|Legen Sie den Datenquellentyp auf `XML` fest. Die Verbindungszeichenfolge besteht aus einer URL für das XML-Dokument.|  
|XML-Datenquelle, eingebettetes XML-Dokument|*Leer*|Legen Sie den Datenquellentyp auf `XML` fest. Die XML-Daten sind in der Berichtsdefinition eingebettet.|  
  
 Weitere Informationen zu jedem Verbindungstyp finden Sie unter [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS&#41; ](report-data/add-data-from-external-data-sources-ssrs.md) und [von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  

  
##  <a name="Creating"></a> Erstellen von Datenquellen  
 Zum Erstellen einer eingebetteten Datenquelle benötigen Sie eine Verbindungszeichenfolge und die Anmeldeinformationen, die für den Zugriff auf die Daten erforderlich sind. Diese Informationen erhalten Sie normalerweise vom Besitzer der Datenquelle. Die Datenverbindung wird als Teil der Datenquelle in der Berichtsdefinition gespeichert. Die Anmeldeinformationen werden unabhängig von der Verbindung verwaltet. Schrittweise Anweisungen finden Sie unter [hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Einige Anmeldeinformationstypen unterstützen möglicherweise nicht alle vom Berichts-Generator verwendeten Szenarien. Wenn Sie eine Abfrage im Abfrage-Designer ausführen möchten, zeigen Sie die Vorschau eines Berichts auf Ihrem Computer an, wenn keine Verbindung zum Berichtsserver hergestellt ist, und führen Sie den Bericht vom Berichtsserver aus. Sie sollten nach Möglichkeit immer freigegebene Datenquellen verwenden. Die Anmeldeinformationen für eine freigegebene Datenquelle auf dem Berichtsserver können Sie speichern. Weitere Informationen finden Sie unter [Angeben von Anmeldeinformationen im Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
 Um eine freigegebene Datenquelle zu erstellen, müssen Sie Berichts-Manager verwenden, um die Datenquelle direkt auf dem Berichtsserver erstellen oder verwenden Sie eine erstellungsumgebung wie z. B. Berichts-Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [erstellen Sie eine eingebettete oder freigegebene Datenquelle &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md).  
  

  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)  
  
  
