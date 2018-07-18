---
title: Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- expressions [Reporting Services], data sources
- data sources [Reporting Services], connections
- connection strings [Reporting Services]
- shared data sources [Reporting Services]
- Reporting Services, data sources
- logins [Reporting Services]
ms.assetid: 4d8f0ae1-102b-4b3d-9155-fa584c962c9e
caps.latest.revision: 112
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 021028f9c5039c04de522fe98b23f93a3b529eba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292260"
---
# <a name="data-connections-data-sources-and-connection-strings-in-reporting-services"></a>Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services
  Zum Einschließen von Daten in einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] melden möchten, müssen Sie zuerst erstellen *Datenquellen* und *Datasets*. In diesem Thema werden die Typen von Datenquellen und die Vorgehensweise bei der Erstellung von Datenquellen beschrieben. Zudem erhalten Sie wichtige Informationen zu Anmeldeinformationen für Datenquellen. Eine Datenquelle umfasst den Datenquellentyp, Verbindungsinformationen und den Typ der zu verwendenden Anmeldeinformationen. Es gibt zwei Typen von Datenquellen: eingebettet und freigegeben. Eine eingebettete Datenquelle wird im Bericht definiert und nur von diesem Bericht verwendet. Eine freigegebene Datenquelle wird unabhängig von einem Bericht definiert und kann von mehreren Berichten verwendet werden. Weitere Informationen finden Sie unter [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) und [Eingebettete und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  

  
##  <a name="bkmk_data_sources"></a> Eingebettete und freigegebene Datenquellen  
 Der Unterschied zwischen den eingebetteten und den freigegebenen Datenquellen ist die Art der Erstellung, Speicherung und Verwaltung.  
  
-   Erstellen Sie eingebettete oder freigegebene Datenquellen im Berichts-Designer als Teil einer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Projekt. Sie können steuern, ob Sie sie für die Vorschau lokal verwenden oder sie als Teil des Projekts auf einem Berichtsserver oder einer SharePoint-Website bereitstellen möchten. Sie können benutzerdefinierte Datenerweiterungen verwenden, die auf dem Computer und dem Berichtsserver oder der SharePoint-Website installiert wurden, auf dem bzw. der die Berichte bereitgestellt werden.  
  
     Systemadministratoren können zusätzliche Datenverarbeitungserweiterungen und .NET Framework-Datenanbieter installieren und konfigurieren. Weitere Informationen finden Sie unter [Datenverarbeitungserweiterungen und .NET Framework-Datenanbieter &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md).  
  
     Entwickler können mithilfe der <xref:Microsoft.ReportingServices.DataProcessing> -API Datenverarbeitungserweiterungen erstellen, durch die weitere Datenquellentypen unterstützt werden.  
  
-   Wechseln Sie im Berichts-Generator zu einem Berichtsserver oder zu einer SharePoint-Website, und wählen Sie freigegebene Datenquellen aus, oder erstellen Sie eingebettete Datenquellen im Bericht. Freigegebene Datenquellen können nicht in Berichts-Generator erstellt werden. Sie können keine benutzerdefinierten Datenerweiterungen in Berichts-Generator verwenden.  
  
##  <a name="bkmk_DataConnections"></a> Integrierte Datenerweiterungen  
 Standarddatenerweiterungen in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] umfassen die folgenden Typen von Datenverbindungen:  
  
-   Microsoft SQL Server  
  
-   Microsoft SQL Server Analysis Services  
  
-   Microsoft SharePoint-Liste  
  
-   [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   OLE DB  
  
-   Oracle  
  
-   SAP NetWeaver BI  
  
-   Hyperion Essbase  
  
-   Teradata  
  
-   XML  
  
-   ODBC  
  
-   Microsoft BI Semantikmodell für Power View: auf einer SharePoint-Website, die für eine PowerPivot-Katalog konfiguriert wurde und [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], es ist dieser Datenquellentyp verfügbar. Dieser Datenquellentyp wird nur für [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]-Präsentationen verwendet. Weitere Informationen finden Sie unter [Building the Perfect BI Semantic Tabular Models for Power View](http://technet.microsoft.com/video/building-the-perfect-bi-semantic-tabular-models-for-power-view.aspx).  
  
 Eine vollständige Liste der Datenquellen und -versionen, die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt, finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="bkmk_create_data_source"></a> Erstellen einer Datenquelle  
 Zum Erstellen einer Datenquelle benötigen Sie die folgenden Informationen:  
  
-   **Datenquellentyp** der Verbindungstyp, z. B. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Wählen Sie diesen Wert aus der Dropdownliste von Verbindungstypen aus.  
  
-   **Verbindungsinformationen** Verbindungsinformationen umfassen den Namen und den Ort der Datenquelle sowie Verbindungseigenschaften, die jeweils speziell für die verschiedenen Datenanbieter gelten. Die *Verbindungszeichenfolge* ist die Darstellung der Verbindungsinformationen in Textform. Wenn zum Beispiel die Datenquelle eine SQL Server-Datenbank ist, können Sie den Namen der Datenbank angeben. Für eingebettete Datenquellen können Sie auch auf Ausdrücken beruhende Verbindungszeichenfolgen schreiben, die zur Laufzeit ausgewertet werden. Weitere Informationen finden Sie im vorliegenden Thema weiter unten unter [Auf Ausdrücken beruhende Verbindungszeichenfolgen](#Expressions) .  
  
-   **Anmeldeinformationen** Sie geben die Anmeldeinformationen an, die zum Zugriff auf die Daten benötigt werden. Der Datenquellenbesitzer muss Ihnen die erforderlichen Berechtigungen erteilt haben, um sowohl auf die Datenquelle und die bestimmten Daten für die Datenquelle zugreifen zu können. Zum Herstellen einer Verbindung mit der auf einem Netzwerkserver installierten [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)]-Beispieldatenbank müssen Sie über die Berechtigung zum Herstellen einer Verbindung mit dem Server sowie über die Leseberechtigung für den Zugriff auf die Datenbank verfügen.  
  
    > [!NOTE]  
    >  Gemäß Konzeption werden Anmeldeinformationen unabhängig von Datenquellen verwaltet. Anmeldeinformationen, mit denen Sie den Bericht in einem lokalen System in der Vorschau anzeigen, unterscheiden sich u. U. von den Anmeldeinformationen, mit denen Sie den veröffentlichten Bericht anzeigen. Nachdem Sie eine Datenquelle auf dem Berichtsserver oder der SharePoint-Website gespeichert haben, müssen Sie unter Umständen die Anmeldeinformationen ändern, um von diesem Ort aus arbeiten zu können. Weitere Informationen finden Sie unter [Anmeldeinformationen für Datenquellen](#bkmk_credentials).  
  
> [!NOTE]  
>  Beim Erstellen einer eingebetteten Datenquelle für einen Bericht in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], müssen Sie die Datenquelle im Berichts-Designer im Projektmappen-Explorer oder im Bereich Berichtsdaten, aber nicht in Server-Explorer erstellen. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Berichts-Designer unterstützt keine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Datenquellen im Server-Explorer erstellt wurden.  
  
 Im Berichtsdatenbereich werden eingebettete Datenquellen und Verweise auf freigegebene Datenquellen angezeigt, die dem Bericht hinzugefügt wurden. In Berichts-Generator verweist ein freigegebener Datenquellenbezug auf eine freigegebene Datenquelle auf einem Berichtsserver oder einer SharePoint-Website. Im Berichts-Designer verweist eine freigegebene Datenquellenreferenz auf eine freigegebene Datenquelle im Projektmappen-Explorer.  
  
##  <a name="bkmk_credentials"></a> Anmeldeinformationen für Datenquellen  
 Per Konzept ist vorgesehen, dass Anmeldeinformationen unabhängig von den Verbindungsinformationen gespeichert und verwaltet werden können. Anmeldeinformationen werden verwendet, um eine Datenquelle zu erstellen, eine Datasetabfrage auszuführen und einen Bericht in der Vorschau anzuzeigen.  
  
> [!NOTE]  
>  Es wird empfohlen, keine Anmeldeinformationen, z. B. Anmeldenamen und Kennwörter, in die Verbindungseigenschaften der Datenquelle einzuschließen. Verwenden Sie wenn möglich immer freigegebene Datenquellen mit gespeicherten Anmeldeinformationen. Verwenden Sie in einer Erstellungsumgebung die Anmeldeinformationsseite des Dialogfelds **Datenquelle** , um Anmeldeinformationen einzugeben, wenn Sie eine Datenverbindung erstellen oder eine Datasetabfrage ausführen.  
  
 Anmeldeinformationen, die Sie für Datenzugriff vom Computer eingeben, werden sicher in der lokalen Projektkonfigurationsdatei gespeichert und sind für den Computer spezifisch. Wenn Sie die Projektdateien auf einen anderen Computer kopieren, müssen Sie die Anmeldeinformationen für die Datenquelle neu definieren.  
  
 Wenn Sie einen Bericht auf dem Berichtsserver oder der SharePoint-Website bereitstellen, werden die eingebetteten und freigegebenen Datenquellen unabhängig verwaltet. Die erforderlichen Datenquellen-Anmeldeinformationen für den Zugriff auf die Daten auf Ihrem Computer unterscheiden sich u. U. von den Anmeldeinformationen, die für den Zugriff auf die Daten durch den Berichtsserver erforderlich sind.  
  
 ![Beachten Sie](media/rs-fyinote.png "Hinweis")empfiehlt sich zu überprüfen, ob die datenquellenverbindungen weiterhin eine Verbindung herstellen, nachdem Sie einen Bericht veröffentlicht wird. Wenn Sie die Anmeldeinformationen ändern müssen, können Sie sie direkt auf dem Berichtsserver ändern.  
  
 Um die von einem Bericht verwendeten Datenquellen zu ändern, können Sie die Berichtseigenschaften im Berichts-Manager im einheitlichen Modus oder über die Dokumentbibliotheken im SharePoint-Modus ändern. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [Anmeldeinformationen in einer Reporting Services-Datenquelle Store](report-data/store-credentials-in-a-reporting-services-data-source.md) [Store Anmeldeinformationen in einer Reporting Services-Datenquelle](report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
-   [Specify Credential and Connection Information for Report Data Sources (Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen)](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
-   [Specify Connections for Custom Data Processing Extensions (Angeben von Verbindungen für benutzerdefinierte Datenverarbeitungserweiterungen)](report-data/specify-connections-for-custom-data-processing-extensions.md)  
  
-   [Angeben von Anmeldeinformationen im Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md)  
  
-   [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
##  <a name="bkmk_connection_examples"></a> Beispiele für häufige Verbindungszeichenfolgen  
 Verbindungszeichenfolgen sind die Textdarstellung von Verbindungseigenschaften für einen Datenanbieter. In der folgenden Tabelle sind Beispiele von Verbindungszeichenfolgen für verschiedene Datenverbindungstypen aufgeführt.  
  
|**Datenquelle**|**Beispiel**|**Beschreibung**|  
|---------------------|-----------------|---------------------|  
|SQL Server-Datenbank auf dem lokalen Server|`data source="(local)";initial catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server`. Weitere Informationen finden Sie unter [SQL Server-Verbindungstyp &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md).|  
|SQL Server-Datenbank auf dem lokalen Server|`data source="(local)";initial catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server`.|  
|SQL Server-Instanz<br /><br /> Datenbank|`Data Source=localhost\MSSQL10_50.InstanceName; Initial Catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server`.|  
|SQL Server Express-Datenbank|`Data Source=localhost\MSSQL10_50.SQLEXPRESS; Initial Catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server`.|  
|[!INCLUDE[ssSDS](../includes/sssds-md.md)] in der cloud|`Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True`|Legen Sie den Datenquellentyp auf `Windows Azure SQL Database`. Weitere Informationen finden Sie unter [SQL Azure-Verbindungstyp &#40;SSRS&#41;](report-data/sql-azure-connection-type-ssrs.md).|  
|SQL Server Parallel Data Warehouse|`HOST=<IP address>;database= AdventureWorks; port=<port>`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server Parallel Data Warehouse`. Weitere Informationen finden Sie unter [SQL Server Parallel Data Warehouse-Verbindungstyp &#40;SSRS&#41;](report-data/sql-server-parallel-data-warehouse-connection-type-ssrs.md).|  
|Analysis Services-Datenbank auf dem lokalen Server|`data source=localhost;initial catalog=Adventure Works DW`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server Analysis Services`. Weitere Informationen finden Sie unter [Analysis Services-Verbindungstyp für MDX (SSRS)](report-data/analysis-services-connection-type-for-mdx-ssrs.md) oder [Analysis Services-Verbindungstyp für DMX (SSRS)](report-data/analysis-services-connection-type-for-dmx-ssrs.md).|  
|Analysis Services-Datenbank für tabellarische Modelle mit Sales-Perspektive|`Data source=<servername>;initial catalog= Adventure Works DW;cube='Sales’`|Legen Sie den Datenquellentyp auf `Microsoft SQL Server Analysis Services`. Geben Sie den Perspektivennamen in der "cube="-Einstellung an. Weitere Informationen finden Sie unter [Perspectives &#40;SSAS Tabular&#41;](../analysis-services/tabular-models/perspectives-ssas-tabular.md).|  
|Berichtsmodell-Datenquelle auf einem Berichtsserver, der im einheitlichen Modus konfiguriert ist|`Server=http://myreportservername/reportserver; datasource=/models/Adventure Works`|Geben Sie die URL des Berichtsservers oder der Dokumentbibliothek sowie den Pfad des veröffentlichten Modells im Namespace des Berichtsserverordners oder Dokumentbibliotheksordners an. Weitere Informationen finden Sie unter [Berichtsmodellverbindung (SSRS)](report-data/report-model-connection-ssrs.md).|  
|Berichtsmodell-Datenquelle auf einem Berichtsserver, der im integrierten SharePoint-Modus konfiguriert ist|`Server=http://server; datasource=http://server/site/documents/models/Adventure Works.smdl`|Geben Sie die URL des Berichtsservers oder der Dokumentbibliothek sowie den Pfad des veröffentlichten Modells im Namespace des Berichtsserverordners oder Dokumentbibliotheksordners an.|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server|`provider=MSOLAP.2;data source=<remote server name>;initial catalog=FoodMart 2000`|Legen Sie den Datenquellentyp auf `OLE DB Provider for OLAP Services 8.0`.<br /><br /> Sie können eine schnellere Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquellen erzielen, wenn Sie die `ConnectTo`-Eigenschaft auf `8.0` festlegen. Sie können diese Eigenschaft im Dialogfeld **Verbindungseigenschaften** auf der Registerkarte **Erweiterte Eigenschaften** festlegen.|  
|Oracle-Server|`data source=myserver`|Legen Sie den Datenquellentyp auf `Oracle`. Auf dem Computer mit Berichts-Designer und auf dem Berichtsserver müssen die Oracle-Clienttools installiert sein. Weitere Informationen finden Sie unter [Oracle-Verbindungstyp &#40;SSRS&#41;](report-data/oracle-connection-type-ssrs.md).|  
|SAP NetWeaver BI-Datenquelle|`DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Legen Sie den Datenquellentyp auf `SAP NetWeaver BI`. Weitere Informationen finden Sie unter [SAP NetWeaver BI-Verbindungstyp &#40;SSRS&#41;](report-data/sap-netweaver-bi-connection-type-ssrs.md).|  
|Hyperion Essbase-Datenquelle|`Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Legen Sie den Datenquellentyp auf `Hyperion Essbase`. Weitere Informationen finden Sie unter [Hyperion Essbase-Verbindungstyp &#40;SSRS&#41;](report-data/hyperion-essbase-connection-type-ssrs.md).|  
|Teradata-Datenquelle|`data source=`\<NNN>.\<NNN>.\<NNN>.\<NNN>`;`|Legen Sie den Datenquellentyp auf `Teradata`. Die Verbindungszeichenfolge ist eine IP-Adresse (Internet Protocol) in Form von vier Feldern, wobei jedes Feld ein bis drei Ziffern aufweisen kann. Weitere Informationen finden Sie unter [Teradataverbindungstyp (SSRS)](report-data/teradata-connection-type-ssrs.md).|  
|XML-Datenquelle, Webdienst|`data source=http://adventure-works.com/results.aspx`|Legen Sie den Datenquellentyp auf `XML`. Die Verbindungszeichenfolge ist eine URL für einen Webdienst, der Webdienste-Definitionssprache (WSDL) unterstützt. Weitere Informationen finden Sie unter [XML-Verbindungstyp (SSRS)](report-data/xml-connection-type-ssrs.md).|  
|XML-Datenquelle, XML-Dokument|`http://localhost/XML/Customers.xml`|Legen Sie den Datenquellentyp auf `XML`. Die Verbindungszeichenfolge besteht aus einer URL für das XML-Dokument.|  
|XML-Datenquelle, eingebettetes XML-Dokument|*Leer*|Legen Sie den Datenquellentyp auf `XML`. Die XML-Daten sind in der Berichtsdefinition eingebettet.|  
  
 Wenn Sie keine Verbindung herstellen, um einen Bericht mithilfe `localhost`, überprüfen Sie, dass das Netzwerkprotokoll für TCP/IP-Protokoll aktiviert ist. Weitere Informationen finden Sie unter [Konfigurieren von Clientprotokollen](../database-engine/configure-windows/configure-client-protocols.md).  
  
 Weitere Informationen zu den Konfigurationen, die zum Herstellen einer Verbindung mit diesen Datenquellentypen erforderlich sind, finden Sie im spezifischen Datenverbindungsthema unter [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) oder [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="bkmk_special_password_characters"></a> Sonderzeichen in Kennwörtern  
 Wenn Sie eine ODBC- oder SQL-Datenquelle so konfigurieren, dass nach einem Kennwort gefragt oder das Kennwort in die Verbindungszeichenfolge eingeschlossen wird, und ein Benutzer das Kennwort mit Sonderzeichen wie z. B. Satzzeichen eingibt, können die Sonderzeichen von einigen zugrunde liegenden Datenquellentreibern nicht überprüft werden. Wenn Sie den Bericht verarbeiten, ist die Meldung "Kein zulässiges Kennwort" möglicherweise ein Anzeichen für dieses Problem. Falls die Änderung des Kennworts unmöglich ist, können Sie mit dem Datenbankadministrator vereinbaren, dass die entsprechenden Anmeldeinformationen auf dem Server als Teil eines ODBC-System-Datenquellennamens (Data Source Name, DSN) gespeichert werden. Weitere Informationen finden Sie unter "OdbcConnection.ConnectionString" in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
##  <a name="bkmk_Expressions_in_connection_strings"></a> Auf Ausdrücken beruhende Verbindungszeichenfolgen  
 Auf Ausdrücken beruhende Verbindungszeichenfolgen werden zur Laufzeit ausgewertet. Sie können beispielsweise die Datenquelle als Parameter angeben, den Parameterverweis in die Verbindungszeichenfolge einbinden und dem Benutzer das Auswählen einer Datenquelle für den Bericht gestatten. Nehmen Sie beispielsweise an, ein multinationales Unternehmen verfügt über Datenserver in verschiedenen Ländern. Mit einer ausdrucksbasierten Verbindungszeichenfolge kann ein Benutzer, der einen Umsatzbericht ausführt, vor der Ausführung des Berichts eine Datenquelle für ein bestimmtes Land bzw. für eine bestimmte Region auswählen.  
  
 Im folgenden Beispiel wird die Verwendung eines Datenquellenausdrucks in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Verbindungszeichenfolge veranschaulicht. Für das Beispiel wird vorausgesetzt, dass Sie einen Berichtsparameter mit dem Namen `ServerName`erstellt haben:  
  
```  
="data source=" & Parameters!ServerName.Value & ";initial catalog=AdventureWorks"  
```  
  
 Datenquellenausdrücke werden zur Laufzeit oder beim Anzeigen einer Berichtsvorschau verarbeitet. Der Ausdruck muss geschrieben werden, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Halten Sie sich an die folgenden Richtlinien, wenn Sie einen Datenquellenausdruck definieren:  
  
-   Entwerfen Sie den Bericht mithilfe einer statischen Verbindungszeichenfolge. Eine statische Verbindungszeichenfolge bezeichnet eine Verbindungszeichenfolge, die nicht durch einen Ausdruck festgelegt wird (wenn Sie beispielsweise die Schritte zum Erstellen einer berichtsspezifischen oder freigegebenen Datenquelle ausführen, definieren Sie eine statische Verbindungszeichenfolge). Die Verwendung einer statischen Verbindungszeichenfolge ermöglicht es Ihnen, im Berichts-Designer eine Verbindung mit der Datenquelle herzustellen, sodass Sie die Abfrageergebnisse abrufen können, die Sie zum Erstellen des Berichts benötigen.  
  
-   Verwenden Sie keine freigegebene Datenquelle, wenn Sie die Datenquellenverbindung definieren. Es ist nicht möglich, einen Datenquellenausdruck in einer freigegebenen Datenquelle zu verwenden. Sie müssen eine eingebettete Datenquelle für den Bericht definieren.  
  
-   Geben Sie die Anmeldeinformationen getrennt von der Verbindungszeichenfolge an. Sie können gespeicherte Anmeldeinformationen, auf Anforderung eingegebene Anmeldeinformationen oder die integrierte Sicherheit verwenden.  
  
-   Fügen Sie einen Berichtsparameter zum Angeben einer Datenquelle hinzu. Als Parameterwerte können Sie entweder eine statische Liste verfügbarer Werte angeben (in diesem Fall sollten die verfügbaren Werte den Datenquellen entsprechen, die Sie mit dem Bericht verwenden können) oder eine Abfrage definieren, die zur Laufzeit eine Liste mit Datenquellen abruft.  
  
-   Stellen Sie sicher, dass die Datenquellen in der Liste das gleiche Datenbankschema verwenden. Die Schemainformationen stellen den Ausgangspunkt bei jedem Berichtsentwurf dar. Wenn das Schema, das zum Definieren des Berichts verwendet wird, nicht mit dem Schema identisch ist, das zur Laufzeit vom Bericht verwendet wird, kann der Bericht möglicherweise nicht ausgeführt werden.  
  
-   Ersetzen Sie die statische Verbindungszeichenfolge durch einen Ausdruck, bevor Sie den Bericht veröffentlichen. Ersetzen Sie die statische Verbindungszeichenfolge erst dann durch einen Ausdruck, wenn der Entwurf des Berichts vollständig abgeschlossen ist. Sobald Sie einen Ausdruck verwenden, können Sie die Abfrage nicht mehr im Berichts-Designer ausführen. Außerdem werden die Feldliste im Berichtsdatenbereich und die Parameterliste nicht mehr automatisch aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Verwalten von Berichtsdatenquellen](report-data/manage-report-data-sources.md)   
 [Eigenschaften im Dialogfeld Datenquelle, Anmeldeinformationen](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)   
 [Freigegebene Eigenschaften im Dialogfeld Datenquelle, Anmeldeinformationen](../../2014/reporting-services/shared-data-source-properties-dialog-box-credentials.md)   
 [Erstellen, ändern und Löschen von freigegebenen Datenquellen &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Festlegen von Bereitstellungseigenschaften &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
  
