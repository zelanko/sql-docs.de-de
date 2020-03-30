---
title: Entwickeln mit XMLA in Analysis Services | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 27b143a9cc5c888c6e464d300d2ccfea114ef9bc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80380681"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Entwickeln mit XMLA in Analysis Services
  XML for Analysis (XMLA) ist ein SOAP-basiertes (Simple Object Access Protocol) XML-Protokoll, das speziell auf den universellen Datenzugriff für jede standardmäßige, mehrdimensionale Datenquelle ausgerichtet ist, auf die mit einer HTTP-Verbindung zugegriffen werden kann. Beim Kommunizieren mit Clientanwendungen wird XMLA als einziges Protokoll von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet. Im Grunde formulieren alle von Analysis Services unterstützten Clientbibliotheken Anforderungen und Antworten in XMLA.  
  
 Als Entwickler können Sie eine Clientanwendung mithilfe von XMLA in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] integrieren, und zwar ohne Abhängigkeiten von .NET Framework oder COM-Schnittstellen. Anwendungsanforderungen, die das Hosten auf vielen Plattformen einschließen, können mit XMLA und einer HTTP-Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt werden.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erfüllt vollständig die 1.1-Spezifikation von XMLA, aber erweitert sie auch, um Datendefinition, Datenbearbeitung und Datensteuerelementunterstützung zu ermöglichen. Analysis Services-Erweiterungen werden als Analysis Services Scripting Language (ASSL) bezeichnet. Die gemeinsame Verwendung von XMLA und ASSL ermöglicht einen größeren Satz an Funktionalitäten und bietet damit mehr Möglichkeiten als XMLA. Weitere Informationen zu ASSL finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Beschreibt, wie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz hergestellt wird und wie Sitzungen und Statusbehaftung in XMLA verwaltet werden.|  
|[Umgang mit Fehlern und Warnungen &#40;XMLA-&#41;](handling-errors-and-warnings-xmla.md)|Beschreibt, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Fehler und Warninformationen für Methoden und Befehle in XMLA zurückgibt.|  
|[Definieren und Identifizieren von Objekten &#40;XMLA-&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Beschreibt Objektbezeichner und Objektverweise und erläutert, wie Bezeichner und Verweise innerhalb von XMLA-Befehlen verwendet werden.|  
|[Verwalten von Transaktionen &#40;XMLA-&#41;](managing-transactions-xmla.md)|Erläutert die Verwendung der Befehle [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)und [RollbackTransaction,](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) um eine Transaktion in der aktuellen XMLA-Sitzung explizit zu definieren und zu verwalten.|  
|[Abbrechen von Befehlen &#40;XMLA-&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Beschreibt, wie der Befehl [Abbrechen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)zum Abbrechen von Befehlen, Sitzungen und Verbindungen in XMLA verwendet wird.|  
|[Ausführen von Batchvorgängen &#40;XMLA-&#41;](performing-batch-operations-xmla.md)|Beschreibt, wie der [Batch-Befehl](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) verwendet wird, um mehrere XMLA-Befehle in seriell oder parallel auszuführen, entweder innerhalb derselben Transaktion oder als separate Transaktionen, mit einer einzelnen XMLA [Execute-Methode.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)|  
|[Erstellen und Ändern von Objekten &#40;XMLA-&#41;](creating-and-altering-objects-xmla.md)|Beschreibt, wie Sie die Befehle [Erstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)und [Löschen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) zusammen mit ASSL-Elementen (Analysis Services Scripting Language) verwenden, um Objekte aus einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz zu definieren, zu ändern oder zu entfernen.|  
|[Sperren und Entsperren von Datenbanken &#40;XMLA-&#41;](locking-and-unlocking-databases-xmla.md)|Details zur Verwendung der [Befehle Sperren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [Entsperren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) zum Sperren und Entsperren einer Datenbank.|  
|[Verarbeiten von Objekten &#40;XMLA&#41;](processing-objects-xmla.md)|Beschreibt, wie der [Befehl](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) Prozess [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zum Verarbeiten eines Objekts verwendet wird.|  
|[Zusammenführen von Partitionen &#40;XMLA-&#41;](merging-partitions-xmla.md)|Beschreibt, wie der Befehl [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) zum [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Zusammenführen von Partitionen auf einer Instance verwendet wird.|  
|[Entwerfen von Aggregationen &#40;XMLA-&#41;](designing-aggregations-xmla.md)|Beschreibt die Verwendung des [Befehls DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) im iterativen modus oder im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Batchmodus zum Entwerfen von Aggregationen für einen Aggregationsentwurf in .|  
|[Sichern, Wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Beschreibt die Verwendung [der](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) Sicherungs- und [Wiederherstellungsbefehle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) zum Sichern und Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer Sicherungsdatei.<br /><br /> Beschreibt außerdem, wie [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) Sie den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Befehl Synchronisieren verwenden, um eine Datenbank mit einer vorhandenen Datenbank auf derselben Instanz oder auf einer anderen Instanz zu synchronisieren.|  
|[Einfügen, Aktualisieren und Löschen von Mitgliedern &#40;XMLA-&#41;](inserting-updating-and-dropping-members-xmla.md)|Beschreibt, wie Die Befehle [Einfügen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Aktualisieren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)und [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) verwendet werden, um Elemente aus einer schreibaktivierten Dimension hinzuzufügen, zu ändern oder zu löschen.|  
|[Aktualisieren von Zellen &#40;XMLA-&#41;](updating-cells-xmla.md)|Beschreibt, wie der Befehl [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) verwendet wird, um die Werte von Zellen in einer schreibaktivierten Partition zu ändern.|  
|[Verwalten von Caches &#40;XMLA-&#41;](managing-caches-xmla.md)|Erläutert die Verwendung des [ClearCache-Befehls](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zum Löschen der Caches von Objekten.|  
|[Überwachen von Traces &#40;XMLA-&#41;](monitoring-traces-xmla.md)|Beschreibt, wie sie den Befehl [Abonnieren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) verwenden, um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine vorhandene Ablaufverfolgung für eine Instance zu abonnieren und zu überwachen.|  
  
## <a name="data-mining-with-xmla"></a>Data Mining mit XMLA  
 XML for Analysis bietet vollständige Unterstützung für Data Mining-Schemarowsets. Diese Rowsets stellen Informationen zum Abfragen von Dataminingmodellen mithilfe der [Discover-Methode](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) bereit. Weitere Informationen zu Data Mining-Schemarowsets finden Sie unter [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
 Weitere Informationen zu DMX finden Sie unter [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Namespace und Schema  
  
### <a name="namespace"></a>Namespace  
 Das in dieser Spezifikation definierte Schema `https://schemas.microsoft.com/AnalysisServices/2003/Engine` verwendet den XML-Namespace und die Standardabkürzung "DDL".  
  
### <a name="schema"></a>Schema  
 Die Definition eines XSD-Schemas (XML Schema Definition) für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Objektdefinitionssprache basiert auf der Definition der Schemaelemente und Hierarchie in diesem Abschnitt.  
  
## <a name="extensibility"></a>Erweiterungen  
 Die Erweiterung des Schemas der Objektdefinitionssprache wird über das `Annotation`-Element bereitgestellt, das in allen Objekten vorhanden ist. Dieses Element kann gemäß den folgenden Regeln jeglichen gültigen XML-Code aus jedem XML-Namespace (außer dem Zielnamespace, der den DDL definiert) enthalten:  
  
-   XML kann nur Elemente enthalten.  
  
-   Jedes Element muss einen eindeutigen Namen haben. Es wird empfohlen, dass der Wert von `Name` auf den Zielnamespace verweist.  
  
 Diese Regeln werden so auferlegt, dass die Inhalte des `Annotation`-Tags als Menge von Name/Wert-Paaren über Decision Support Objects (DSO) 9.0 verfügbar gemacht werden können.  
  
 Kommentare und Leerzeichen innerhalb des `Annotation`-Tags, die nicht mit einem untergeordneten Element eingeschlossen sind, können nicht beibehalten werden. Darüber hinaus müssen alle Elemente lese-write sein; Schreibgeschützte Elemente werden ignoriert.  
  
 Das Schema der Objektdefinitionssprache ist insofern geschlossen, dass der Server nicht zulässt, dass abgeleitete Typen durch im Schema definierte Elemente ersetzt werden. Daher akzeptiert der Server nur die hier definierte Gruppe an Elementen und keine anderen Elemente oder Attribute. Unbekannte Elemente bewirken, dass die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Engine einen Fehler auslöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwicklung mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Grundlegendes zur Microsoft OLAP-Architektur](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
