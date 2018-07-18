---
title: Abfragedesigner in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
caps.latest.revision: 16
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aed7304b4e7e48eff1691970da5ff68b03fd0962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222940"
---
# <a name="reporting-services-query-designers"></a>Abfrage-Designer in Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Stellt grafische und textbasierte Abfrage-Designer Sie Abfragen für jeden Datenquellentyp in Ihrem Bericht erstellen können.  
  
 Einige Datenquellen unterstützen grafische Designer, mit denen Sie eine Abfrage interaktiv erstellen können. Andere Datenquellen verwenden einen textbasierten Abfrage-Designer. Bei einem grafischen Abfrage-Designer können Sie Metadatenelemente, die die zugrunde liegenden Daten einer Datenquelle darstellen, auf die Entwurfsoberfläche der Abfrage ziehen. Bei einem textbasierten Abfrage-Designer können Sie den Befehlstext in einen Abfragebereich eingeben. Sie können von einem grafischen Abfrage-Designer zu einem textbasierten Abfrage-Designer wechseln, indem Sie auf der Symbolleiste auf das Symbol für den textbasierten Abfrage-Designer klicken.  
  
 Welche Datenquellentypen in Ihrem Bericht verfügbar sind, wird durch die auf dem Client oder Berichtsserver installierten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Erweiterungen bestimmt. Weitere Informationen finden Sie unter [RSReportDesigner-Konfigurationsdatei](report-server/rsreportdesigner-configuration-file.md) und [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md).  
  
 Eine Datenverarbeitungserweiterung und der zugehörige Abfrage-Designer können sich hinsichtlich der Unterstützung für Datenquellen auf folgende Weisen unterscheiden:  
  
-   **Hinsichtlich des Abfrage-Designer-Typs.** Eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquelle unterstützt z. B. sowohl grafische als auch textbasierte Abfrage-Designer.  
  
-   **Hinsichtlich der Abfragesprachenvariation.** Eine Abfragesprache wie [!INCLUDE[tsql](../includes/tsql-md.md)] kann zum Beispiel je nach Datenquellentyp in der Syntax variieren. Die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] -Sprache und die Oracle SQL-Sprache unterscheiden sich in der Syntax für einen Abfragebefehl.  
  
-   **Hinsichtlich der Unterstützung für den Schemateil des Namens eines Datenbankobjekts.** Wenn in einer Datenquelle Schemas als Teil des Datenbankobjektbezeichners verwendet werden, muss der Schemaname als Teil der Abfrage für Namen angegeben werden, für die das Standardschema nicht verwendet wird. Beispiel: `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **Hinsichtlich der Unterstützung für Abfrageparameter.** Datenanbieter unterscheiden sich in der Unterstützung für Parameter. Einige Datenanbieter unterstützen benannte Parameter, beispielsweise `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Einige Datenanbieter unterstützen unbenannte Parameter, beispielsweise `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. Der Parameterbezeichner kann vom Datenanbieter unterscheiden sich. z. B. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet die "at" (@) Symbol "," Oracle verwendet den Doppelpunkt (:)). Einige Datenanbieter unterstützen keine Parameter.  
  
-   **Hinsichtlich der Fähigkeit zum Importieren von Abfragen.** Sie können z. B. für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquelle eine Abfrage aus einer Berichtsdefinitionsdatei (.rdl) oder aus einer SQL-Datei importieren.  
  
## <a name="query-designers"></a>Abfrage-Designer  
 In den folgenden Themen wird die Benutzeroberfläche für die einzelnen Abfrage-Designer beschrieben.  
  
-   [Analysis Services MDX Query Designer User Interface (Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services)](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Analysis Services DMX Query Designer User Interface (Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services)](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [Graphical Query Designer User Interface (Grafische Benutzeroberfläche des Abfrage-Designers)](report-data/graphical-query-designer-user-interface.md)  
  
-   [Relational Query Designer User Interface (Benutzeroberfläche des relationalen Abfrage-Designers)](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Hyperion Essbase Query Designer User Interface (Benutzeroberfläche des Abfrage-Designers von Hyperion Essbase)](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [Report Model Query Designer User Interface (Benutzeroberfläche des Berichtsmodellabfrage-Designers)](report-data/report-model-query-designer-user-interface.md)  
  
-   [SAP NetWeaver BI Query Designer User Interface (Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI)](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [SharePoint List Query Designer (Designer für SharePoint-Listenabfragen)](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [Text-based Query Designer User Interface (Benutzeroberfläche des textbasierten Abfrage-Designers)](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Hinzufügen von Daten aus externen Datenquellen (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md)   
 [Datenverarbeitungserweiterungen und .NET Framework-Datenanbieter &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [Erweiterungen &#40;SSRS&#41;](extensions-ssrs.md)  
  
  
