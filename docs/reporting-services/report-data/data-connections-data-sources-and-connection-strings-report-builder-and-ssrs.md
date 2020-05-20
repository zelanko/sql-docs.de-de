---
title: Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 11/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 73bf9e24ffb42ef93547097c53b5838a22292fda
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74190912"
---
# <a name="create-data-connection-strings---report-builder--ssrs"></a>Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Sie müssen zuerst eine *Zeichenfolge* in Ihrer *Datenquelle* erstellen, um Daten in paginierten Berichten von [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] einzuschließen. In diesem Artikel wird beschrieben, wie Sie Datenverbindungszeichenfolgen erstellen. Zudem erhalten Sie wichtige Informationen zu Anmeldeinformationen für Datenquellen. Eine Datenquelle umfasst den Datenquellentyp, Verbindungsinformationen und den Typ der zu verwendenden Anmeldeinformationen. Weitere Informationen finden Sie unter [Einführung in Berichtsdaten in SQL Server Reporting Services (SSRS)](report-data-ssrs.md).
  
##  <a name="built-in-data-extensions"></a><a name="bkmk_DataConnections"></a> Integrierte Datenerweiterungen  
 Standarddatenerweiterungen in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthalten Microsoft SQL Server, Microsoft Azure SQL-Datenbank und SQL Server Analysis Services. Eine vollständige Liste der Datenquellen und -versionen, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt, finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
##  <a name="common-connection-string-examples"></a><a name="bkmk_connection_examples"></a> Beispiele für häufige Verbindungszeichenfolgen  
 Verbindungszeichenfolgen sind die Textdarstellung von Verbindungseigenschaften für einen Datenanbieter. In der folgenden Tabelle sind Beispiele von Verbindungszeichenfolgen für verschiedene Datenverbindungstypen aufgeführt.  
 
 > [!NOTE]  
>  [Connectionstrings.com](https://www.connectionstrings.com/) ist eine weitere Ressource für den Bezug von Verbindungszeichenfolgen. 
  
|**Datenquelle**|**Beispiel**|**Beschreibung**|  
|---------------------|-----------------|---------------------|  
|SQL Server-Datenbank auf dem lokalen Server|`data source="(local)";initial catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf **Microsoft SQL Server**fest. Weitere Informationen finden Sie unter [SQL Server-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/sql-server-connection-type-ssrs.md).|  
|SQL Server-Instanz<br /><br /> database|`Data Source=localhost\MSSQL13.<InstanceName>; Initial Catalog=AdventureWorks`|Legen Sie den Datenquellentyp auf **Microsoft SQL Server**fest.|  
|Azure SQL-Datenbank|`Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True`|Legen Sie den Datenquellentyp auf **Microsoft Azure SQL-Datenbank** fest. Weitere Informationen finden Sie unter [SQL Azure-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/sql-azure-connection-type-ssrs.md).|  
|SQL Server Parallel Data Warehouse|`HOST=<IP address>;database= AdventureWorks; port=<port>`|Legen Sie den Datenquellentyp auf **Microsoft SQL Server Parallel Data Warehouse**fest. Weitere Informationen finden Sie unter [SQL Server Parallel Data Warehouse-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/sql-server-parallel-data-warehouse-connection-type-ssrs.md).|  
|Analysis Services-Datenbank auf dem lokalen Server|`data source=localhost;initial catalog=Adventure Works DW`|Legen Sie den Datenquellentyp auf **Microsoft SQL Server Analysis Services**fest. Weitere Informationen finden Sie unter [Analysis Services-Verbindungstyp für MDX (SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md) oder [Analysis Services-Verbindungstyp für DMX (SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md).|  
|Analysis Services-Datenbank für tabellarische Modelle mit Sales-Perspektive|`Data source=<servername>;initial catalog= Adventure Works DW;cube='Sales'`|Legen Sie den Datenquellentyp auf **Microsoft SQL Server Analysis Services**fest. Geben Sie den Perspektivennamen in der "cube="-Einstellung an. Weitere Informationen finden Sie unter [Perspektiven &#40;SSAS – tabellarisch&#41;](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular).|  
|Oracle-Server|`data source=myserver`|Legen Sie den Datenquellentyp auf **Oracle**fest. Auf dem Computer mit Berichts-Designer und auf dem Berichtsserver müssen die Oracle-Clienttools installiert sein. Weitere Informationen finden Sie unter [Oracle-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/oracle-connection-type-ssrs.md).|  
|SAP NetWeaver BI-Datenquelle|`DataSource=https://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Legen Sie den Datenquellentyp auf **SAP NetWeaver BI**fest. Weitere Informationen finden Sie unter [SAP NetWeaver BI-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/sap-netweaver-bi-connection-type-ssrs.md).|  
|Hyperion Essbase-Datenquelle|`Data Source=https://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Legen Sie den Datenquellentyp auf **Hyperion Essbase**fest. Weitere Informationen finden Sie unter [Hyperion Essbase-Verbindungstyp &#40;SSRS&#41;](../../reporting-services/report-data/hyperion-essbase-connection-type-ssrs.md).|  
|Teradata-Datenquelle|`data source=`\<NNN>.\<NNN>.\<NNN>.\<NNN>`;`|Legen Sie den Datenquellentyp auf **Teradata**fest. Die Verbindungszeichenfolge ist eine IP-Adresse (Internet Protocol) in Form von vier Feldern, wobei jedes Feld ein bis drei Ziffern aufweisen kann. Weitere Informationen finden Sie unter [Teradataverbindungstyp (SSRS)](../../reporting-services/report-data/teradata-connection-type-ssrs.md).|  
|Teradata-Datenquelle|`Database=` *\<database name>* `; data source=` *\<NN*N *>.\<NNN>.\<NNN>.\<N*NN *>* `;Use X Views=False;Restrict to Default Database=True`|Legen Sie den Datenquellentyp auf **Teradata**fest, ähnlich dem vorherigen Beispiel. Verwenden Sie nur die Standarddatenbank, die im Datenbank-Tag angegeben wird, und ermitteln Sie nicht automatisch Datenbeziehungen.|  
|XML-Datenquelle, Webdienst|`data source=https://adventure-works.com/results.aspx`|Legen Sie den Datenquellentyp auf **XML**fest. Die Verbindungszeichenfolge ist eine URL für einen Webdienst, der Webdienste-Definitionssprache (WSDL) unterstützt. Weitere Informationen finden Sie unter [XML-Verbindungstyp (SSRS)](../../reporting-services/report-data/xml-connection-type-ssrs.md).|  
|XML-Datenquelle, XML-Dokument|`https://localhost/XML/Customers.xml`|Legen Sie den Datenquellentyp auf **XML**fest. Die Verbindungszeichenfolge besteht aus einer URL für das XML-Dokument. 
|XML-Datenquelle, eingebettetes XML-Dokument|*Leer*|Legen Sie den Datenquellentyp auf **XML**fest. Die XML-Daten sind in der Berichtsdefinition eingebettet.|  
|SharePoint-Liste|`data source=https://MySharePointWeb/MySharePointSite/`|Legen Sie den Datenquellentyp auf **SharePoint-Liste**fest.|  
| Power BI Premium-Dataset (ab Reporting Services 2019) | Server=powerbi://api.powerbi.com/v1.0/myorg/<workspacename>;initial catalog = <YourDatasetName> | Legen Sie den Datenquellentyp auf **Microsoft SQL Server Analysis Services**fest. |

  
 Wenn Sie mittels **localhost**keine Verbindung zu einem Berichtsserver herstellen können, überprüfen Sie, ob das Netzwerkprotokoll für TCP/IP aktiviert ist. Weitere Informationen finden Sie unter [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).  
  
 Weitere Informationen zu den Konfigurationen, die zum Herstellen einer Verbindung mit diesen Datenquellentypen erforderlich sind, finden Sie im spezifischen Datenverbindungsartikel unter [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md) oder [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
##  <a name="special-characters-in-a-password"></a><a name="bkmk_special_password_characters"></a> Sonderzeichen in Kennwörtern  
 Wenn Sie eine ODBC- oder SQL-Datenquelle so konfigurieren, dass nach einem Kennwort gefragt oder das Kennwort in die Verbindungszeichenfolge eingeschlossen wird, und ein Benutzer das Kennwort mit Sonderzeichen wie z. B. Satzzeichen eingibt, können die Sonderzeichen von einigen zugrunde liegenden Datenquellentreibern nicht überprüft werden. Wenn Sie den Bericht verarbeiten, ist die Meldung "Kein zulässiges Kennwort" möglicherweise ein Anzeichen für dieses Problem. Falls die Änderung des Kennworts unmöglich ist, können Sie mit dem Datenbankadministrator vereinbaren, dass die entsprechenden Anmeldeinformationen auf dem Server als Teil eines ODBC-System-Datenquellennamens (Data Source Name, DSN) gespeichert werden. Weitere Informationen finden Sie unter [Eigenschaft „OdbcConnection.ConnectionString“](https://docs.microsoft.com/dotnet/api/system.data.odbc.odbcconnection.connectionstring) in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Dokumentation.  
  
##  <a name="expression-based-connection-strings"></a><a name="bkmk_Expressions_in_connection_strings"></a> Auf Ausdrücken basierende Verbindungszeichenfolgen  
 Auf Ausdrücken beruhende Verbindungszeichenfolgen werden zur Laufzeit ausgewertet. Sie können beispielsweise die Datenquelle als Parameter angeben, den Parameterverweis in die Verbindungszeichenfolge einbinden und dem Benutzer das Auswählen einer Datenquelle für den Bericht gestatten. Nehmen Sie beispielsweise an, ein multinationales Unternehmen verfügt über Datenserver in verschiedenen Ländern. Mit einer ausdrucksbasierten Verbindungszeichenfolge kann ein Benutzer, der einen Umsatzbericht ausführt, vor der Ausführung des Berichts eine Datenquelle für ein bestimmtes Land bzw. für eine bestimmte Region auswählen.  
  
 Im folgenden Beispiel wird die Verwendung eines Datenquellenausdrucks in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungszeichenfolge veranschaulicht. Für das Beispiel wird vorausgesetzt, dass Sie einen Berichtsparameter mit dem Namen `ServerName`erstellt haben:  
  
```  
="data source=" & Parameters!ServerName.Value & ";initial catalog=AdventureWorks"  
```  
  
 Datenquellenausdrücke werden zur Laufzeit oder beim Anzeigen einer Berichtsvorschau verarbeitet. Der Ausdruck muss in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]geschrieben sein. Halten Sie sich an die folgenden Richtlinien, wenn Sie einen Datenquellenausdruck definieren:  
  
-   Entwerfen Sie den Bericht mithilfe einer statischen Verbindungszeichenfolge. Eine statische Verbindungszeichenfolge bezeichnet eine Verbindungszeichenfolge, die nicht durch einen Ausdruck festgelegt wird (wenn Sie beispielsweise die Schritte zum Erstellen einer berichtsspezifischen oder freigegebenen Datenquelle ausführen, definieren Sie eine statische Verbindungszeichenfolge). Die Verwendung einer statischen Verbindungszeichenfolge ermöglicht es Ihnen, im Berichts-Designer eine Verbindung mit der Datenquelle herzustellen, sodass Sie die Abfrageergebnisse abrufen können, die Sie zum Erstellen des Berichts benötigen.  
  
-   Verwenden Sie keine freigegebene Datenquelle, wenn Sie die Datenquellenverbindung definieren. Es ist nicht möglich, einen Datenquellenausdruck in einer freigegebenen Datenquelle zu verwenden. Sie müssen eine eingebettete Datenquelle für den Bericht definieren.  
  
-   Geben Sie die Anmeldeinformationen getrennt von der Verbindungszeichenfolge an. Sie können gespeicherte Anmeldeinformationen, auf Anforderung eingegebene Anmeldeinformationen oder die integrierte Sicherheit verwenden.  
  
-   Fügen Sie einen Berichtsparameter zum Angeben einer Datenquelle hinzu. Als Parameterwerte können Sie entweder eine statische Liste verfügbarer Werte angeben (in diesem Fall sollten die verfügbaren Werte den Datenquellen entsprechen, die Sie mit dem Bericht verwenden können) oder eine Abfrage definieren, die zur Laufzeit eine Liste mit Datenquellen abruft.  
  
-   Stellen Sie sicher, dass die Datenquellen in der Liste das gleiche Datenbankschema verwenden. Die Schemainformationen stellen den Ausgangspunkt bei jedem Berichtsentwurf dar. Wenn das Schema, das zum Definieren des Berichts verwendet wird, nicht mit dem Schema identisch ist, das zur Laufzeit vom Bericht verwendet wird, kann der Bericht möglicherweise nicht ausgeführt werden.  
  
-   Ersetzen Sie die statische Verbindungszeichenfolge durch einen Ausdruck, bevor Sie den Bericht veröffentlichen. Ersetzen Sie die statische Verbindungszeichenfolge erst dann durch einen Ausdruck, wenn der Entwurf des Berichts vollständig abgeschlossen ist. Sobald Sie einen Ausdruck verwenden, können Sie die Abfrage nicht mehr im Berichts-Designer ausführen. Außerdem werden die Feldliste im Berichtsdatenbereich und die Parameterliste nicht mehr automatisch aktualisiert.  

## <a name="next-steps"></a>Nächste Schritte

[Einführung in Berichtsdaten in SQL Server Reporting Services (SSRS)](report-data-ssrs.md)
[Erstellen und Ändern von freigegebenen Datenquellen](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
[Erstellen und Verwenden eingebetteter Datenquellen](../../reporting-services/report-data/create-and-modify-embedded-data-sources.md)   
[Festlegen von Bereitstellungseigenschaften](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
[Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
