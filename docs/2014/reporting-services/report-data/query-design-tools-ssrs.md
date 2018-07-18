---
title: Abfrageentwurfstools im Berichts-Designer SQL Server Data Tools (SSRS) | Microsoft-Dokumentation
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
- graphical query designer [Reporting Services]
- MDX query designer [Reporting Services]
- text-based query designer [Reporting Services]
- DMX [Reporting Services]
- query designers [Reporting Services]
- generic query designer See text-based query designer
- Reporting Services, query designers
- semantic queries [Reporting Services]
- Report Model Query Designer
ms.assetid: a8139a9d-4aeb-4e64-96f3-564edf60479f
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4721d0df4f1c6d8f5a0dda8c70d90b0134c62fbc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264216"
---
# <a name="query-design-tools-in-report-designer-sql-server-data-tools-ssrs"></a>Abfrageentwurfstools in SQL Server-Datentools (SSRS) des Berichts-Designers
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt eine Reihe von Abfrageentwurfstools bereit, mit denen Sie im Berichts-Designer Datasetabfragen erstellen können. Ob ein bestimmter Abfrage-Designer verfügbar ist, hängt von dem Typ der Datenquelle ab, mit der Sie arbeiten. Darüber hinaus stellen einige Abfrage-Designer alternative Modi bereit, sodass Sie entscheiden können, ob Sie im visuellen Modus oder direkt in der Abfragesprache arbeiten möchten. In diesem Thema werden die einzelnen Tools sowie die von ihnen unterstützten Datenquellen beschrieben. Folgende Tools werden in diesem Thema vorgestellt:  
  
-   [Textbasierter Abfrage-Designer](#Textbased)  
  
-   [Grafischer Abfrage-Designer](#Graphical)  
  
-   [Berichtsmodellabfrage-Designer](#Model)  
  
-   [MDX-Abfrage-Designer](#MDX)  
  
-   [DMX-Abfrage-Designer](#DMX)  
  
-   [SapNetWeaver BI Abfrage-Designer](#SAPBW)  
  
-   [MDX-Abfrage-Designer von Hyperion Essbase](#Hyperion)  
  
 Wenn Sie mit einer Berichtsserver-Projektvorlage oder einer Vorlage des Berichtsserverprojekt-Assistenten arbeiten, werden alle Abfrageentwurfstools in der Datenentwurfsumgebung von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ausgeführt. Weitere Informationen zum Arbeiten mit Abfrage-Designern finden Sie unter [Reporting Services Query Designers](../reporting-services-query-designers.md).  
  
##  <a name="Textbased"></a> Textbasierter Abfrage-Designer  
 Der textbasierte Abfrage-Designer ist das Standardtool zum Erstellen von Abfragen für die meisten unterstützten relationalen Datenquellen, einschließlich [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], Oracle, Teradata, OLE DB, XML und ODBC. Im Gegensatz zum grafischen Abfrage-Designer wird bei diesem Abfrageentwurfstools die Abfragesyntax während des Abfrageentwurfs nicht überprüft. In der folgenden Grafik wird der textbasierte Abfrage-Designer veranschaulicht.  
  
 ![Generischer Abfrage-Designer für relationale Datenabfragen](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")  
  
 Der textbasierte Abfrage-Designer wird zum Erstellen komplexer Abfragen unter Verwendung gespeicherter Prozeduren, zum Abfragen von XML-Daten und zum Schreiben dynamischer Abfragen empfohlen. Je nach Datenquelle können Sie möglicherweise die Schaltfläche **Als Text bearbeiten** auf der Symbolleiste aktivieren bzw. deaktivieren, um zwischen dem grafischen und dem textbasierten Abfrage-Designer zu wechseln. Weitere Informationen finden Sie unter [Benutzeroberfläche des textbasierten Abfrage-Designers](../text-based-query-designer-user-interface.md).  
  
##  <a name="Graphical"></a> Grafischer Abfrage-Designer  
 Der grafische Abfrage-Designer dient zum Erstellen oder Ändern von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen, die für die relationale Datenbank ausgeführt werden. Dieses Abfrageentwurfstool wird in mehreren [!INCLUDE[msCoName](../../../includes/msconame-md.md)]-Produkten und anderen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Komponenten verwendet. Abhängig vom Datenquellentyp unterstützt es Modi für Text, StoredProcedure und TableDirect. In der folgenden Grafik wird der grafische Abfrage-Designer veranschaulicht.  
  
 ![Graphischer Abfrage-Designer für SQL-Abfrage](../media/rsqd-dsaw-sql.gif "Graphical query designer for sql query")  
  
 Sie können auf der Symbolleiste die Schaltfläche **Als Text bearbeiten** aktivieren oder deaktivieren, um zwischen dem textbasierten und dem grafischen Abfrage-Designer zu wechseln. Weitere Informationen finden Sie unter [Graphical Query Designer User Interface](graphical-query-designer-user-interface.md).  
  
##  <a name="Model"></a> Berichtsmodellabfrage-Designer  
 Der Berichtsmodellabfrage-Designer wird zum Erstellen oder Ändern von Abfragen verwendet, die für ein auf einem Berichtsserver veröffentlichtes SMDL-Berichtsmodell ausgeführt werden. Berichte, die für Modelle ausgeführt werden, unterstützen die Datendurchsuchung mittels Durchklicken. Die Abfrage bestimmt den Pfad der Datendurchsuchung zur Laufzeit. In der folgenden Grafik wird der Berichtsmodellabfrage-Designer veranschaulicht.  
  
 ![Benutzeroberfläche des Abfrage-Designers für semantische Modelle](../media/rsqd-dsawmodel-smql.gif "Semantic Model Query Designer UI")  
  
 Wenn Sie den Berichtsmodellabfrage-Designer verwenden möchten, müssen Sie eine Datenquelle definieren, die auf ein veröffentlichtes Modell zeigt. Wenn Sie ein Dataset für die Datenquelle definieren, können Sie die Dataset-Abfrage im Berichtsmodellabfrage-Designer öffnen. Der Berichtsmodellabfrage-Designer kann im grafischen oder im textbasierten Modus verwendet werden. Sie können auf der Symbolleiste die Schaltfläche **Als Text bearbeiten** aktivieren oder deaktivieren, um zwischen dem textbasierten und dem grafischen Abfrage-Designer zu wechseln. Weitere Informationen finden Sie unter [Report Model Query Designer User Interface](report-model-query-designer-user-interface.md).  
  
##  <a name="MDX"></a> MDX-Abfrage-Designer  
 Der MDX-Abfrage-Designer (Multidimensional Expression) dient zum Erstellen oder Ändern von Abfragen, die für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle mit mehrdimensionalen Cubes ausgeführt werden. In der folgenden Grafik wird der MDX-Abfrage-Designer nach dem Definieren der Abfrage und der Filter veranschaulicht.  
  
 ![Analysis Services-MDX-Abfrage-Designer, Entwurfsansicht](../../analysis-services/media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX query designer, design view")  
  
 Wenn Sie den MDX-Abfrage-Designer verwenden möchten, müssen Sie nach einer Datenquelle suchen, die einen verfügbaren Analysis Service-Cube aufweist, der gültig ist und verarbeitet wurde. Wenn Sie ein Dataset für die Datenquelle definieren, können Sie die Abfrage im MDX-Abfrage-Designer öffnen. Falls erforderlich, können Sie die MDX- und DMX-Schaltfläche auf der Symbolleiste verwenden, um zwischen MDX- und DMX-Modus zu wechseln. Weitere Informationen finden Sie unter [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).  
  
##  <a name="DMX"></a> DMX-Abfrage-Designer  
 Der Data Mining Prediction Expression (DMX)-Abfrage-Designer dient zum Erstellen oder Ändern von Abfragen, die für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle mit Miningmodellen ausgeführt werden. In der folgenden Grafik wird der DMX-Abfrage-Designer nach der Auswahl des Modells und der Eingabetabellen veranschaulicht.  
  
 ![Analysis Services-DMX-Abfrage-Designer, Entwurfsansicht](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")  
  
 Wenn Sie den DMX-Abfrage-Designer verwenden möchten, müssen Sie eine Datenquelle definieren, die ein gültiges, verfügbares Data Mining-Modell aufweist. Wenn Sie ein Dataset für die Datenquelle definieren, können Sie die Abfrage im DMX-Abfrage-Designer öffnen. Falls erforderlich, können Sie die MDX- und DMX-Schaltfläche auf der Symbolleiste verwenden, um zwischen MDX- und DMX-Modus zu wechseln. Nachdem Sie das Modell ausgewählt haben, können Sie Data Mining-Vorhersageabfragen erstellen, die Daten für einen Bericht bereitstellen. Weitere Informationen finden Sie unter [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).  
  
##  <a name="SAPBW"></a> SapNetWeaver BI Abfrage-Designer  
 Der [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] -Abfrage-Designer dient zum Abrufen von Daten aus einer [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] -Datenbank. Um diesen Abfrage-Designer verwenden zu können, benötigen Sie ein [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] -Datenquelle, mindestens eine Infocube-, Multiprovider- oder webfähige Abfrage definiert ist. In der folgenden Grafik wird der [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] -Abfrage-Designer veranschaulicht.  
  
 ![Abfrage-Designer mit MDX im Entwurfsmodus](../media/rsqd-dssapbw-mdx-designmode.gif "Query Designer using MDX in Design Mode")  
  
##  <a name="Hyperion"></a> MDX-Abfrage-Designer von Hyperion Essbase  
 Der [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Abfrage-Designer dient zum Abrufen von Daten aus [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Datenbanken und -Anwendungen. In der folgenden Grafik wird der [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Abfrage-Designer veranschaulicht.  
  
 ![Abfrage-Designer für Hyperion Essbase-Datenquelle](../media/rsqd-dshyperionessbase-mdx-designmode.gif "Query Designer for Hyperion Essbase data source")  
  
 Wenn Sie diesen Abfrage-Designer verwenden möchten, benötigen Sie eine [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Datenquelle mit mindestens einer Datenbank. Weitere Informationen finden Sie unter [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Tools](../tools/reporting-services-tools.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Reporting Services-Tutorials (SSRS)](../reporting-services-tutorials-ssrs.md)   
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Erstellen einer eingebetteten oder freigegebenen Datenquelle &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)  
  
  
