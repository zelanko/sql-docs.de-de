---
title: Entwickeln mit XMLA in Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 2f5455b71306b3dd75406f107e5c1e971f6b923b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545002"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Entwickeln mit XMLA in Analysis Services
  XML for Analysis (XMLA) ist ein SOAP-basiertes (Simple Object Access Protocol) XML-Protokoll, das speziell auf den universellen Datenzugriff für jede standardmäßige, mehrdimensionale Datenquelle ausgerichtet ist, auf die mit einer HTTP-Verbindung zugegriffen werden kann. Beim Kommunizieren mit Clientanwendungen wird XMLA als einziges Protokoll von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet. Im Grunde formulieren alle von Analysis Services unterstützten Clientbibliotheken Anforderungen und Antworten in XMLA.  
  
 Als Entwickler können Sie eine Clientanwendung mithilfe von XMLA in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] integrieren, und zwar ohne Abhängigkeiten von .NET Framework oder COM-Schnittstellen. Anwendungsanforderungen, die das Hosten auf vielen Plattformen einschließen, können mit XMLA und einer HTTP-Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt werden.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt vollständig die 1.1-Spezifikation von XMLA, aber erweitert sie auch, um Datendefinition, Datenbearbeitung und Datensteuerelementunterstützung zu ermöglichen. Analysis Services-Erweiterungen werden als Analysis Services Scripting Language (ASSL) bezeichnet. Die gemeinsame Verwendung von XMLA und ASSL ermöglicht einen größeren Satz an Funktionalitäten und bietet damit mehr Möglichkeiten als XMLA. Weitere Informationen zu ASSL finden Sie unter [entwickeln mit Analysis Services Skriptsprache &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Beschreibt, wie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz hergestellt wird und wie Sitzungen und Statusbehaftung in XMLA verwaltet werden.|  
|[Behandeln von Fehlern und Warnungen &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Beschreibt, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Fehler und Warninformationen für Methoden und Befehle in XMLA zurückgibt.|  
|[Definieren und Identifizieren von Objekten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Beschreibt Objektbezeichner und Objektverweise und erläutert, wie Bezeichner und Verweise innerhalb von XMLA-Befehlen verwendet werden.|  
|[Verwalten von Transaktionen &#40;XMLA&#41;](managing-transactions-xmla.md)|Erläutert, wie die Befehle [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)und [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) verwendet werden, um eine Transaktion in der aktuellen XMLA-Sitzung explizit zu definieren und zu verwalten.|  
|[Abbrechen von Befehlen &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Beschreibt, wie der [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)-Befehl verwendet wird, um Befehle, Sitzungen und Verbindungen in XMLA abzubrechen.|  
|[Ausführen von Batch Vorgängen &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Beschreibt, wie der [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) -Befehl verwendet wird, um mehrere XMLA-Befehle in seriell oder parallel auszuführen, entweder innerhalb derselben Transaktion oder als separate Transaktionen, wobei eine einzelne XMLA- [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methode verwendet wird.|  
|[Erstellen und Ändern von Objekten &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Beschreibt, wie die Befehle [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)und [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) zusammen mit Analysis Services-Skriptsprache (ASSL)-Elementen verwendet werden, um Objekte von einer-Instanz zu definieren, zu ändern oder zu entfernen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Sperren und Entsperren von Datenbanken &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Erläutert, wie die Befehle [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) und [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) zum Sperren und Entsperren einer Datenbank verwendet werden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Verarbeiten von Objekten &#40;XMLA&#41;](processing-objects-xmla.md)|Beschreibt, wie der [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) -Befehl verwendet wird, um ein Objekt zu verarbeiten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Zusammenführen von Partitionen &#40;XMLA&#41;](merging-partitions-xmla.md)|Beschreibt, wie der [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) -Befehl verwendet wird, um Partitionen auf einer-Instanz zusammenzuführen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Entwerfen von Aggregationen &#40;XMLA&#41;](designing-aggregations-xmla.md)|Beschreibt, wie der [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) -Befehl entweder im iterativen oder im Batch Modus zum Entwerfen von Aggregationen für einen Aggregationen Entwurf in verwendet wird [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Sichern, Wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Beschreibt, wie die Befehle [Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) und [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) verwendet werden, um eine- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer Sicherungsdatei zu sichern und wiederherzustellen.<br /><br /> Außerdem wird beschrieben, wie Sie mithilfe des [Synchronisierungs](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) Befehls eine- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank mit einer vorhandenen Datenbank auf derselben-Instanz oder einer anderen-Instanz synchronisieren.|  
|[Einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Beschreibt, wie die Befehle [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)und [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) zum Hinzufügen, ändern oder Löschen von Elementen in einer Dimension mit aktiviertem Schreibzugriff verwendet werden.|  
|[Aktualisieren von Zellen &#40;XMLA&#41;](updating-cells-xmla.md)|Beschreibt, wie der [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) -Befehl verwendet wird, um die Werte von Zellen in einer Partition mit aktiviertem Schreibzugriff zu ändern.|  
|[Verwalten von Caches &#40;XMLA&#41;](managing-caches-xmla.md)|Erläutert, wie der [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) -Befehl verwendet wird, um die Caches von Objekten zu löschen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Überwachen von Ablauf Verfolgungen &#40;XMLA&#41;](monitoring-traces-xmla.md)|Beschreibt, wie der [subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) -Befehl verwendet wird, um eine vorhandene Ablauf Verfolgung auf einer-Instanz zu abonnieren und zu überwachen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
  
## <a name="data-mining-with-xmla"></a>Data Mining mit XMLA  
 XML for Analysis bietet vollständige Unterstützung für Data Mining-Schemarowsets. Diese Rowsets enthalten Informationen zum Abfragen von Data Mining Modellen mithilfe der [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) -Methode. Weitere Informationen zu Data Mining Schemarowsets finden Sie unter [Data Mining-Schemarowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) . 
  
 Weitere Informationen zu DMX finden Sie unter [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Namespace und Schema  
  
### <a name="namespace"></a>Namespace  
 Das in dieser Spezifikation definierte Schema verwendet den XML-Namespace `https://schemas.microsoft.com/AnalysisServices/2003/Engine` und die Standard Abkürzung "DDL".  
  
### <a name="schema"></a>Schema  
 Die Definition eines XSD-Schemas (XML Schema Definition) für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objektdefinitionssprache basiert auf der Definition der Schemaelemente und Hierarchie in diesem Abschnitt.  
  
## <a name="extensibility"></a>Erweiterungen  
 Die Erweiterung des Schemas der Objektdefinitionssprache wird über das `Annotation`-Element bereitgestellt, das in allen Objekten vorhanden ist. Dieses Element kann gemäß den folgenden Regeln jeglichen gültigen XML-Code aus jedem XML-Namespace (außer dem Zielnamespace, der den DDL definiert) enthalten:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, dass der Wert von `Name` auf den Zielnamespace verweist.  
  
 Diese Regeln werden so auferlegt, dass die Inhalte des `Annotation`-Tags als Menge von Name/Wert-Paaren über Decision Support Objects (DSO) 9.0 verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des `Annotation`-Tags, die nicht mit einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Außerdem müssen alle Elemente über Lese-/Schreibzugriff verfügen. schreibgeschützte Elemente werden ignoriert.  
  
 Das Schema der Objektdefinitionssprache ist insofern geschlossen, dass der Server nicht zulässt, dass abgeleitete Typen durch im Schema definierte Elemente ersetzt werden. Daher akzeptiert der Server nur die hier definierte Gruppe an Elementen und keine anderen Elemente oder Attribute. Unbekannte Elemente bewirken, dass die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Engine einen Fehler auslöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit Analysis Services Skriptsprache &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Grundlegendes zur Microsoft OLAP-Architektur](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
