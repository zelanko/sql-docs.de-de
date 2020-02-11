---
title: Reporting Services Abfrage-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c004b098f900606c2263391cf9363b6e5be2b97b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102881"
---
# <a name="reporting-services-query-designers"></a>Abfrage-Designer in Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] stellt grafische und textbasierte Abfrage-Designer bereit, um Ihnen das Erstellen von Abfragen für alle Datenquellentypen in Ihrem Bericht zu erleichtern.  
  
 Einige Datenquellen unterstützen grafische Designer, mit denen Sie eine Abfrage interaktiv erstellen können. Andere Datenquellen verwenden einen textbasierten Abfrage-Designer. Bei einem grafischen Abfrage-Designer können Sie Metadatenelemente, die die zugrunde liegenden Daten einer Datenquelle darstellen, auf die Entwurfsoberfläche der Abfrage ziehen. Bei einem textbasierten Abfrage-Designer können Sie den Befehlstext in einen Abfragebereich eingeben. Sie können von einem grafischen Abfrage-Designer zu einem textbasierten Abfrage-Designer wechseln, indem Sie auf der Symbolleiste auf das Symbol für den textbasierten Abfrage-Designer klicken.  
  
 Welche Datenquellentypen in Ihrem Bericht verfügbar sind, wird durch die auf dem Client oder Berichtsserver installierten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Erweiterungen bestimmt. Weitere Informationen finden Sie unter [RSReportDesigner-Konfigurationsdatei](report-server/rsreportdesigner-configuration-file.md) und [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md).  
  
 Eine Datenverarbeitungserweiterung und der zugehörige Abfrage-Designer können sich hinsichtlich der Unterstützung für Datenquellen auf folgende Weisen unterscheiden:  
  
-   **Nach dem Typ des Abfrage-Designers.** Eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquelle unterstützt z. B. sowohl grafische als auch textbasierte Abfrage-Designer.  
  
-   **Abfrage Sprachen Variation.** Eine Abfragesprache wie [!INCLUDE[tsql](../includes/tsql-md.md)] kann zum Beispiel je nach Datenquellentyp in der Syntax variieren. Die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] Sprache und die Oracle SQL-Sprache haben einige Variationen der Syntax für einen Abfragebefehl.  
  
-   **Durch die Unterstützung für den Schema Teil des Namens eines Datenbankobjekts.** Wenn in einer Datenquelle Schemas als Teil des Datenbankobjektbezeichners verwendet werden, muss der Schemaname als Teil der Abfrage für Namen angegeben werden, für die das Standardschema nicht verwendet wird. Beispiel: `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **Durch Unterstützung von Abfrage Parametern.** Datenanbieter unterscheiden sich in der Unterstützung für Parameter. Einige Datenanbieter unterstützen benannte Parameter, beispielsweise `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Einige Datenanbieter unterstützen unbenannte Parameter, beispielsweise `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. Der Parameterbezeichner kann je nach Datenanbieter unterschiedlich sein. Beispielsweise wird in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] das Symbol @ und in Oracle der Doppelpunkt (:) verwendet. Einige Datenanbieter unterstützen keine Parameter.  
  
-   **Durch die Möglichkeit zum Importieren von Abfragen.** Sie können z. B. für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquelle eine Abfrage aus einer Berichtsdefinitionsdatei (.rdl) oder aus einer SQL-Datei importieren.  
  
## <a name="query-designers"></a>Abfrage-Designer  
 In den folgenden Themen wird die Benutzeroberfläche für die einzelnen Abfrage-Designer beschrieben.  
  
-   [Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [Grafische Benutzeroberfläche des Abfrage-Designers](report-data/graphical-query-designer-user-interface.md)  
  
-   [Benutzeroberfläche des relationalen Abfrage-Designers](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Benutzeroberfläche des Abfrage-Designers von Hyperion Essbase](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [Benutzeroberfläche des Berichtsmodellabfrage-Designers](report-data/report-model-query-designer-user-interface.md)  
  
-   [Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [Designer für SharePoint-Listenabfragen](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [Benutzeroberfläche des textbasierten Abfrage-Designers](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen, die von Reporting Services &#40;SSRS unterstützt werden&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS-&#41;](report-data/add-data-from-external-data-sources-ssrs.md)   
 [Datenverarbeitungs Erweiterungen und .NET Framework-Datenanbieter &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [Erweiterungen &#40;SSRS&#41;](extensions-ssrs.md)  
  
  
