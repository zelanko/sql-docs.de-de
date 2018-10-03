---
title: Entwickeln mit XMLA in Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d88bbd891591b28db840b3b9e90ae74120ba625a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170200"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Entwickeln mit XMLA in Analysis Services
  XML for Analysis (XMLA) ist ein SOAP-basiertes (Simple Object Access Protocol) XML-Protokoll, das speziell auf den universellen Datenzugriff für jede standardmäßige, mehrdimensionale Datenquelle ausgerichtet ist, auf die mit einer HTTP-Verbindung zugegriffen werden kann. Beim Kommunizieren mit Clientanwendungen wird XMLA als einziges Protokoll von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet. Im Grunde formulieren alle von Analysis Services unterstützten Clientbibliotheken Anforderungen und Antworten in XMLA.  
  
 Als Entwickler können Sie eine Clientanwendung mithilfe von XMLA in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] integrieren, und zwar ohne Abhängigkeiten von .NET Framework oder COM-Schnittstellen. Anwendungsanforderungen, die das Hosten auf vielen Plattformen einschließen, können mit XMLA und einer HTTP-Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt werden.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt vollständig die 1.1-Spezifikation von XMLA, aber erweitert sie auch, um Datendefinition, Datenbearbeitung und Datensteuerelementunterstützung zu ermöglichen. Analysis Services-Erweiterungen werden als Analysis Services Scripting Language (ASSL) bezeichnet. Die gemeinsame Verwendung von XMLA und ASSL ermöglicht einen größeren Satz an Funktionalitäten und bietet damit mehr Möglichkeiten als XMLA. Weitere Informationen über ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Beschreibt, wie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz hergestellt wird und wie Sitzungen und Statusbehaftung in XMLA verwaltet werden.|  
|[Behandeln von Fehlern und Warnungen &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Beschreibt, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Fehler und Warninformationen für Methoden und Befehle in XMLA zurückgibt.|  
|[Definieren und Identifizieren von Objekten &#40;XMLA&#41;](../xmla/xml-elements-objects.md)|Beschreibt Objektbezeichner und Objektverweise und erläutert, wie Bezeichner und Verweise innerhalb von XMLA-Befehlen verwendet werden.|  
|[Verwalten von Transaktionen &#40;XMLA&#41;](managing-transactions-xmla.md)|Informationen zur Verwendung der [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md), und [RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) Befehle aus, um explizit zu definieren und Verwalten einer Transaktions auf der aktuellen XMLA Sitzung.|  
|[Abbrechen von Befehlen &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Beschreibt, wie die [Abbrechen](../xmla/xml-elements-commands/cancel-element-xmla.md)Befehl aus, um Befehle, Sitzungen und Verbindungen in XMLA abzubrechen.|  
|[Ausführen von Batchvorgängen &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Beschreibt, wie die [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) Befehl zum Ausführen von mehrere XMLA-Befehle seriell oder parallel, entweder innerhalb derselben Transaktion oder als separate Transaktionen, die mit einer einzigen XMLA- [Execute](../xmla/xml-elements-methods-execute.md) Methode.|  
|[Erstellen und Ändern von Objekten &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Beschreibt, wie die [erstellen](../xmla/xml-elements-commands/create-element-xmla.md), [Alter](../xmla/xml-elements-commands/alter-element-xmla.md), und [löschen](../xmla/xml-elements-commands/delete-element-xmla.md) Befehle aus, zusammen mit Analysis Services Scripting Language (ASSL)-Elemente, um zu definieren, ändern oder entfernen Objekte aus einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz.|  
|[Sperren und Entsperren von Datenbanken &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Erläutert, wie die [Sperre](../xmla/xml-elements-commands/lock-element-xmla.md) und [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) Befehle aus, um Sperren und Entsperren einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank.|  
|[Verarbeiten von Objekten &#40;XMLA&#41;](processing-objects-xmla.md)|Beschreibt, wie die [Prozess](../xmla/xml-elements-commands/process-element-xmla.md) Befehl Prozess eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekt.|  
|[Zusammenführen von Partitionen &#40;XMLA&#41;](merging-partitions-xmla.md)|Beschreibt, wie die [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) Befehl zum Zusammenführen von Partitionen auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz.|  
|[Entwerfen von Aggregationen &#40;XMLA&#41;](designing-aggregations-xmla.md)|Beschreibt, wie die [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) -Befehl entweder im iterativen oder im Batchmodus verwendet, zum Entwerfen von Aggregationen für einen Aggregationsentwurf in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Beschreibt, wie die [Backup](../xmla/xml-elements-commands/backup-element-xmla.md) und [wiederherstellen](../xmla/xml-elements-commands/restore-element-xmla.md) Befehle zum Sichern und Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer Sicherungsdatei.<br /><br /> Außerdem beschreibt, wie die [synchronisieren](../xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl aus, um die Synchronisierung eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank mit einer vorhandenen Datenbank auf derselben Instanz oder auf einer anderen Instanz.|  
|[Einfügen, aktualisieren und Löschen von Elementen &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Beschreibt, wie die [einfügen](../xmla/xml-elements-commands/insert-element-xmla.md), [Update](../xmla/xml-elements-commands/update-element-xmla.md), und [löschen](../xmla/xml-elements-commands/drop-element-xmla.md) Befehle hinzufügen, ändern oder Löschen von Mitgliedern aus einer Dimension mit aktiviertem Schreibzugriff.|  
|[Aktualisieren von Zellen &#40;XMLA&#41;](updating-cells-xmla.md)|Beschreibt, wie die [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) Befehl aus, um die Werte der Zellen in einer Partition mit aktiviertem Schreibzugriff zu ändern.|  
|[Verwalten von Caches &#40;XMLA&#41;](managing-caches-xmla.md)|Informationen zur Verwendung der [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) Befehl aus, um die Caches von löschen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekte.|  
|[Überwachen von Ablaufverfolgungen &#40;XMLA&#41;](monitoring-traces-xmla.md)|Beschreibt, wie die [abonnieren](../xmla/xml-elements-commands/subscribe-element-xmla.md) Befehl abonnieren und Überwachen eine vorhandene Ablaufverfolgung auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz.|  
  
## <a name="data-mining-with-xmla"></a>Data Mining mit XMLA  
 XML for Analysis bietet vollständige Unterstützung für Data Mining-Schemarowsets. Diese Rowsets finden Sie Informationen zum Abfragen von Datamining-Modellen mithilfe der [Discover](../xmla/xml-elements-methods-discover.md) Methode. Weitere Informationen zu Datamining-Schemarowsets, finden Sie unter [Data Mining Schema Rowsets](../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
 Weitere Informationen zu DMX finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; Verweis](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Namespace und Schema  
  
### <a name="namespace"></a>Namespace  
 In dieser Spezifikation definierte Schema verwendet den XML-Namespace http://schemas.microsoft.com/AnalysisServices/2003/Engine und die standardabkürzung "DDL".  
  
### <a name="schema"></a>Schema  
 Die Definition eines XSD-Schemas (XML Schema Definition) für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objektdefinitionssprache basiert auf der Definition der Schemaelemente und Hierarchie in diesem Abschnitt.  
  
## <a name="extensibility"></a>Erweiterbarkeit  
 Die Erweiterung des Schemas der Objektdefinitionssprache wird über das `Annotation`-Element bereitgestellt, das in allen Objekten vorhanden ist. Dieses Element kann gemäß den folgenden Regeln jeglichen gültigen XML-Code aus jedem XML-Namespace (außer dem Zielnamespace, der den DDL definiert) enthalten:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, dass der Wert von `Name` auf den Zielnamespace verweist.  
  
 Diese Regeln werden so auferlegt, dass die Inhalte des `Annotation`-Tags als Menge von Name/Wert-Paaren über Decision Support Objects (DSO) 9.0 verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des `Annotation`-Tags, die nicht mit einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Darüber hinaus müssen alle Elemente über Lese-und Schreibberechtigung aufweisen; Schreibgeschützte Elemente werden ignoriert.  
  
 Das Schema der Objektdefinitionssprache ist insofern geschlossen, dass der Server nicht zulässt, dass abgeleitete Typen durch im Schema definierte Elemente ersetzt werden. Daher akzeptiert der Server nur die hier definierte Gruppe an Elementen und keine anderen Elemente oder Attribute. Unbekannte Elemente bewirken, dass die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Engine einen Fehler auslöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Grundlegendes zur Microsoft OLAP-Architektur](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
