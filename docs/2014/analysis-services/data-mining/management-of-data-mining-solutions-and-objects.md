---
title: Verwaltung von Data Mining-Lösungen und-Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae3e672932dd320c6b369f23f03c1f056d30d4ba
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522176"
---
# <a name="management-of-data-mining-solutions-and-objects"></a>Verwaltung von Data Mining-Lösungen und -Objekten
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] stellt Clienttools bereit, mit denen Sie vorhandene Miningstrukturen und Miningmodelle verwalten können. In diesem Abschnitt werden die Verwaltungsvorgänge beschrieben, die Sie mit der jeweiligen Umgebung ausführen können.  
  
 Außer mit diesen Tools können Data Mining-Objekte auch programmgesteuert mithilfe von AMO oder mit anderen Clients verwaltet werden, die eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank herstellen können, wie etwa mit den Data Mining Add-Ins für [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verschieben von Data Mining-Objekten](moving-data-mining-objects.md)  
  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md)  
  
 [Verwenden von SQL Server Profiler zum Überwachen von Data Mining &#40;Analysis Services – Data Mining&#41;](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a>Speicherort von Data Mining-Objekten  
 Verarbeitete Miningstrukturen und -modelle werden in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]gespeichert.  
  
 Wenn Sie eine Verbindung mit einer- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank im- `Immediate` Modus erstellen, wenn Sie die Data Mining Objekte entwickeln, werden alle Objekte, die Sie erstellen, sofort dem Server hinzugefügt, wenn Sie arbeiten. Wenn Data Mining-Objekte im **Offline** -Modus erstellt werden, dem Standardmodus bei der Arbeit in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dann sind die erstellten Miningobjekte so lange nur Metadatencontainer, bis sie auf einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitgestellt werden. Jedes Mal, wenn ein Objekt verändert wird, muss es daher erneut auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server bereitgestellt werden. Weitere Informationen zur Datamining-Architektur finden Sie unter [Physische Architektur &#40;Analysis Services – Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Einige Clients, z.B. die Data Mining Add-Ins für [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, ermöglichen auch die Erstellung von Miningmodellen und -strukturen als Sitzungsobjekte, für die eine Verbindung mit einer Instanz verwendet wird, deren Miningstrukturen und -modelle jedoch auf dem Server nur für die Dauer der Sitzung gespeichert werden. Diese Modelle können ebenso mit dem Client verwaltet werden wie die in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank gespeicherten Strukturen und Modelle, aber die Objekte werden nicht persistent gespeichert, nachdem die Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz getrennt wurde.  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a>Verwalten von Data Mining-Objekten in SQL Server-Datentools  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] bietet Funktionen, die das Erstellen, Durchsuchen und Bearbeiten von Data Mining-Objekten erleichtern.  
  
 Die folgenden Links enthalten Informationen darüber, wie Sie Data Mining-Objekte mit [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ändern können:  
  
-   [Bearbeiten der für eine Miningstruktur verwendeten Datenquellensicht](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [Ändern der Eigenschaften einer Miningstruktur](change-the-properties-of-a-mining-structure.md)  
  
-   [Ändern der Eigenschaften eines Miningmodells](change-the-properties-of-a-mining-model.md)  
  
-   [Anzeigen oder Ändern von Modellierungsflags &#40;Data Mining&#41;](modeling-flags-data-mining.md)  
  
-   [Anzeigen oder Ändern von Algorithmusparametern](view-or-change-algorithm-parameters.md)  
  
 In der Regel verwenden Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] als Tool zum Entwickeln von neuen Projekten und zum Hinzufügen zu vorhandenen Projekten. Sie verwalten dann Projekte und Objekte, die mit Tools wie z. B. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bereitgestellt wurden.  
  
 Sie können Objekte, die bereits auf einer Instanz von ssASnoversion mit der `Immediate`-Option bereitgestellt werden, und das Herstellen einer Verbindung mit dem Server im Onlinemodus jedoch direkt ändern. Weitere Informationen finden Sie unter [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
> [!WARNING]  
>  Alle Änderungen an einer Miningstruktur oder einem Miningmodell, selbst Änderungen an Metadaten wie Name oder Beschreibung, machen es erforderlich, dass die Miningstruktur bzw. das -modell erneut verarbeitet wird.  
  
 Wenn Sie die Projektmappendatei nicht haben, die verwendet wurde, um das Data Mining-Projekt oder die -Objekte zu erstellen, können Sie das vorhandene Projekt vom Server importieren, der den Analysis Services-Import-Assistenten verwendet. Außerdem können Sie Änderungen an den Objekten vornehmen und diese dann mit der `Incremental`-Option erneut bereitstellen. Weitere Informationen finden Sie unter [Importieren eines Data Mining-Projekts mithilfe des Analysis Services-Import-Assistenten](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a>Verwalten von Data Mining-Objekten in SQL Server Management Studio  
 In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie Skripts für Miningstrukturen und -modelle schreiben, Miningstrukturen und -modelle verarbeiten oder löschen. Im Objektexplorer wird nur ein eingeschränkter Satz an Eigenschaften angezeigt. Sie können jedoch zusätzliche Metadaten zu Miningmodellen anzeigen, indem Sie das Fenster **DMX-Abfrage** öffnen und eine Miningstruktur auswählen.  
  
-   [Erstellen einer DMX-Abfrage in SQL Server Management Studio](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a>Programmgesteuertes Verwalten von Data Mining-Objekten  
 Mit den folgenden Programmiersprachen können Data Mining-Objekte erstellt, geändert, verarbeitet und gelöscht werden. Jede Sprache wurde für verschiedene Tasks entwickelt. Daher kann es Beschränkungen hinsichtlich des Typs der ausführbaren Vorgänge geben. Einige Eigenschaften der Data Mining-Objekte können z. B. nicht mit DMX (Data Mining Extensions) geändert werden. Sie müssen stattdessen XMLA oder AMO verwenden.  
  
### <a name="analysis-management-objects-amo"></a>Analysis Management Objects (AMO)  
 Analysis Management Object (AMO) ist ein Objektmodell, das auf XMLA aufsetzt und Ihnen einen Vollzugriff auf Data Mining-Objekte erlaubt. Durch die Verwendung von AMO können Sie Miningstrukturen und Miningmodelle erstellen, bereitstellen und überwachen.  
  
-   [AMO-Konzepte und-Objektmodell](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **Einschränkungen:** Keine.  
  
### <a name="data-mining-extensions-dmx"></a>Data Mining-Erweiterungen (DMX)  
 Data Mining-Erweiterungen (DMX) können in Kombination mit anderen Befehlsschnittstellen wie [!INCLUDE[vstecado](../../includes/vstecado-md.md)] oder ADOMD.NET verwendet werden, um Miningstrukturen und Miningmodelle zu erstellen, zu löschen und abzufragen.  
  
-   [Data Mining-Erweiterungen &#40;DMX&#41; – Datendefinitionsanweisungen](/sql/dmx/dmx-statements-data-definition)  
  
 **Einschränkungen:** Einige Eigenschaften können mit DMX nicht geändert werden.  
  
### <a name="xml-for-analysis-xmla"></a>XML for Analysis (XMLA)  
 XML for Analysis (XMLA) ist die Datendefinitionssprache für sämtliche Analysis Services. XMLA ermöglicht es Ihnen, die meisten der Data Mining-Objekte und Servervorgänge zu steuern. Alle Verwaltungsvorgänge zwischen Client und Server können mit XMLA ausgeführt werden. Zur Vereinfachung können Sie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Skriptsprache (ASSL) verwenden, um das XML einzubinden.  
  
 **Einschränkungen:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generiert einige XMLA-Anweisungen, die nur für die interne Verwendung unterstützt werden und in XML DDL-Skripts nicht verwendet werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwicklerhandbuch &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)  
  
  
