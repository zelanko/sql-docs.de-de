---
title: Analysis Services im tabellarischen Modell Partitionen | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e8fbbfe1aaf7c97a5739768413cdc04644be6a6
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072647"
---
# <a name="tabular-model-partitions"></a>Tabellenmodellpartitionen 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Durch Partitionen wird eine Tabelle logisch unterteilt. Jede Partition kann unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden. Während der Modellerstellung werden die für ein Modell definierten Partitionen in ein bereitgestelltes Modell dupliziert. Nach der Bereitstellung können Sie diese Partitionen mit dem Dialogfeld **Partitionen** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mithilfe eines Skripts verwalten. In diesem Thema werden Partitionen in einer Datenbank für bereitgestellte tabellarische Modelle beschrieben. Weitere Informationen zum Erstellen und Verwalten von Partitionen während der Modellerstellung finden Sie unter [Partitionen](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_benefits)  
  
-   [Berechtigungen](#bkmk_permissions)  
  
-   [Partitionen verarbeiten](#bkmk_process_partitions)  
  
-   [Parallelverarbeitung](#bkmk_parallelProc)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> Vorteile  
 Bei einem effizienten Modellentwurf werden Partitionen genutzt, um unnötige Verarbeitungsschritte und die daraus resultierende Belastung der Analysis Services-Serverprozessoren zu eliminieren und gleichzeitig sicherzustellen, dass bestimmte Daten so häufig verarbeitet und aktualisiert werden, dass immer die neuesten Daten aus den Datenquellen bereitgestellt werden.  
  
 Ein tabellarisches Modell kann beispielsweise über eine Sales-Tabelle verfügen, die Umsatzzahlen für das laufende Geschäftsjahr 2011 und jedes vorangehende Geschäftsjahr umfasst. Das Modell der Tabelle "Sales" hat die folgenden drei Partitionen:  
  
|Partition|Daten aus|  
|---------------|---------------|  
|Sales2011|Aktuelles Geschäftsjahr|  
|Sales2010-2001|Geschäftsjahre 2001, 2002, 2003, 2004, 2005, 2006. 2007, 2008, 2009, 2010|  
|SalesOld|Alle Geschäftsjahre vor den letzten zehn Jahren.|  
  
 Während neue Umsatzzahlen für das laufende Geschäftsjahr 2011 hinzugefügt werden, müssen die Daten täglich verarbeitet werden, damit sie in der Umsatzanalyse für das laufende Geschäftsjahr entsprechend berücksichtigt werden; die Partition "Sales2011" wird folglich nachts verarbeitet.  
  
 Im Unterschied dazu ist es nicht erforderlich, die Daten der Partition "Sales2010-2001" nachts zu verarbeiten. Da sich die Umsatzzahlen für die vorangegangenen zehn Geschäftsjahre aufgrund von Produktrücksendungen und anderen Anpassungen jedoch ändern können, müssen sie immer noch regelmäßig verarbeitet werden. Die Daten in der Partition "Sales2010-2001" werden folglich monatlich verarbeitet. Die Daten in der Partition "SalesOld" ändern sich nie und werden daher nur jährlich verarbeitet.  
  
 Wenn Sie das Geschäftsjahr 2012 eingeben, wird der Modus des Sales-Tabelle neue Partition "sales2012" hinzugefügt. Die Partition "Sales2011" kann dann mit der Partition "Sales2010-2001" zusammengeführt und in "Sales2011-2002" umbenannt werden. Die Daten aus dem Geschäftsjahr 2001 werden aus der neuen Partition "Sales2011-2002" entfernt und in die Partition "SalesOld" verschoben. Alle Partitionen werden daraufhin verarbeitet, damit die Änderungen berücksichtigt werden.  
  
 Wie Sie eine Partitionsstrategie für tabellarische Modelle Ihrer Organisation implementieren, werden zum größten Teil Ihrer verarbeitungsanforderungen bestimmten Modell und den verfügbaren Ressourcen abhängig sein.  
  
##  <a name="bkmk_permissions"></a> Berechtigungen  
 Damit Sie Partitionen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen, verwalten und verarbeiten können, müssen die entsprechenden Analysis Services-Berichtigungen in einer Sicherheitsrolle definiert sein. Jede Sicherheitsrolle verfügt über eine der folgenden Berechtigungen:  
  
|Berechtigung|Aktionen|  
|----------------|-------------|  
|Administrator|Lesen, Verarbeiten, Erstellen, Kopieren, Zusammenführen, Löschen|  
|Verarbeiten|Lesen, Verarbeiten|  
|Schreibgeschützt|Leseberechtigung|  
  
 Weitere Informationen zum Erstellen von Rollen während der Modellerstellung mithilfe [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], finden Sie unter [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md). Weitere Informationen zum Verwalten von Rollenmitgliedern, für die Rollen bereitgestellter tabellarischer Modelle mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], finden Sie unter [Rollen tabellarischer Modelle](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
##  <a name="bkmk_parallelProc"></a> Parallelverarbeitung  
Analysis Services enthält die parallele Verarbeitung für Tabellen mit zwei oder mehr Partitionen, sodass die verarbeitungsleistung erhöht. Für die Parallelverarbeitung gibt es keine Konfigurationseinstellungen (siehe Hinweise). Die Parallelverarbeitung erfolgt standardmäßig bei der Verarbeitung von Tabellen bzw. wenn Sie für die gleiche Tabelle und den gleichen Prozess mehrere Partitionen auswählen. Dennoch können Sie die Partitionen einer Tabelle weiterhin auch einzeln verarbeiten.  
  
> [!NOTE]  
>  Sie können die Eigenschaftsoption **maxParallism** mit dem [Sequence-Befehl (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/sequence-command-tmsl)verwenden, um anzugeben, ob Aktualisierungsvorgänge sequenziell oder parallel auszuführen sind.

> [!NOTE]  
>  Bei Feststellung einer erneuten Codierung kann die Parallelverarbeitung die Systemressourcen erheblich beanspruchen, da verschiedene Operationen auf den Partitionen unterbrochen und mit der neuen Codierung parallel neu gestartet werden müssen.  
  
##  <a name="bkmk_process_partitions"></a> Partitionen verarbeiten  
 Partitionen können in **mithilfe des Dialogfelds** Partitionen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder mithilfe eines Skripts unabhängig von anderen Partitionen verarbeitet (bzw. aktualisiert) werden. Folgende Optionen stehen für die Verarbeitung zur Verfügung:  
  
|Modus|Description|  
|----------|-----------------|  
|Standard verarbeiten|Erkennt den Verarbeitungsstatus eines Partitionsobjekts und führt die Verarbeitung durch, durch die nicht oder teilweise verarbeitete Partitionsobjekte in den Status "Vollständig verarbeitet" versetzt werden. Daten für leere Tabellen und Partitionen werden geladen, Hierarchien, berechnete Spalten und Beziehungen werden erstellt oder neu erstellt.|  
|Vollständig verarbeiten|Verarbeitet ein Partitionsobjekt und alle darin enthaltenen Objekte. Wenn die Verarbeitungsmethode "Vollständig verarbeiten" für ein bereits verarbeitetes Objekt ausgeführt wird, löscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Daten im Objekt und verarbeitet anschließend das Objekt. Diese Art der Verarbeitung ist erforderlich, wenn eine Änderung an der Objektstruktur vorgenommen wurde.|  
|Daten verarbeiten|Lädt Daten in eine Partition oder Tabelle, ohne Hierarchien oder Beziehungen neu zu erstellen bzw. berechnete Spalten und Measures neu zu berechnen.|  
|Löschung verarbeiten|Entfernt alle Daten aus einer Partition.|  
|Hinzufügung verarbeiten|Aktualisiert die Partition inkrementell mit neuen Daten.|  
  
##  <a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Aufgabe|Description|  
|----------|-----------------|  
|[Erstellen und Verwalten von Tabellenmodellpartitionen](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)|Beschreibt, wie Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Partitionen in einem bereitgestellten tabellarischen Modell erstellen und verwalten.|  
|[Verarbeiten von Tabellenmodellpartitionen](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)|Beschreibt, wie Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Partitionen in einem bereitgestellten tabellarischen Modell verarbeiten.|  
  
  
