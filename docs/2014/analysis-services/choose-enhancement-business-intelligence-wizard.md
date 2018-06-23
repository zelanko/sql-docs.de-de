---
title: Wählen Sie die Erweiterung (Business Intelligence-Assistent) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.biwizard.bienhancement.f1
ms.assetid: 39e2f36c-2c02-4a71-af8f-5dbd373190dc
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1377e93214ff5d9e459698946551ffaed6723390
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161694"
---
# <a name="choose-enhancement-business-intelligence-wizard"></a>Erweiterung auswählen (Business Intelligence-Assistent)
  Auf der Seite **Erweiterung auswählen** wählen Sie die Business Intelligence-Erweiterung aus, die dem Cube oder der Dimension hinzugefügt werden soll.  
  
## <a name="options"></a>Tastatur  
 **Verfügbare Erweiterungen**  
 Wählen Sie die hinzuzufügende Business Intelligence-Erweiterung aus. In der folgenden Tabelle sind die verfügbaren Erweiterungen aufgelistet.  
  
|Erweiterung|Description|  
|-----------------|-----------------|  
|**Zeitintelligenz definieren**|Fügen Sie einer ausgewählten Hierarchie zusätzliche Zeitsichten hinzu. Zu diesen Sichten gehören Zeitraum bis Datum, gleitender Durchschnitt und Zeitraumvergleich.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Definieren der Kontointelligenz**|Weisen Sie Elementen eines Kontoattributs Standardbuchhaltungsklassifikationen, z. B. Einnahmen und Ausgaben, zu.<br /><br /> Wenn die Aggregationsfunktion des Measures auf *ByAccount*festgelegt ist, verwendet die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz die Buchhaltungsklassifikationen, um über einen Zeitraum ein Measure für die Elemente eines Kontoattributs zu aggregieren.|  
|**Dimensionsintelligenz definieren**|Mit der Dimensionsintelligenz geben Sie einen Standardunternehmenstyp für eine Dimension und gültige Typen für die Dimensionsattribute an. Diese Typspezifikationen können von Clientanwendungen bei der Datenanalyse verwendet werden.|  
|**Unäroperator angeben**|Geben Sie einen unären Operator an, um die den Elementen in einer Über-/Unterordnungshierarchie zugeordnete Standardaggregation zu ersetzen.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Erstellen einer benutzerdefinierten Elementformel**|Erstellen Sie eine benutzerdefinierte Elementformel, um die Standardaggregation zu ersetzen, die einem Dimensionselement mit einem anderen Operator zugeordnet ist.|  
|**Attributreihenfolge angeben**|Geben Sie die Reihenfolge der Elemente eines ausgewählten Attributs an. Die Elemente können nach dem Namen oder Schlüssel eines ausgewählten Attributs oder nach dem Namen oder Schlüssel eines mit dem ausgewählten Attribut verknüpften Attributs sortiert werden. Standardmäßig werden Elemente nach dem Namen des ausgewählten Attributs sortiert.|  
|**Aktivieren des Rückschreibens**|Aktivieren Sie die manuelle Änderung der Dimensionsstruktur. Updates für eine Dimension mit aktiviertem Schreibzugriff werden direkt in der Dimensionstabelle aufgezeichnet.|  
|**Semiadditives Verhalten definieren**|Definieren Sie manuell die Aggregationsmethode für einzelne Measures oder Elemente eines Kontotypattributs. Wenn der Cube eine Kontodimension enthält, können Sie das semiadditive Verhalten mithilfe der Option **Kontointelligenz definieren** auf der Grundlage des Kontotyps automatisch festlegen.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Währungsumrechnung definieren**|Definieren Sie Regeln zum Umrechnen und Analysieren multinationaler Daten im Cube. Umrechnungsregeln werden auf Cubeebene mithilfe eines MDX-Skripts (Multidimensional Expressions) angewendet, das vom Business Intelligence-Assistenten generiert wird.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
  
 **Beschreibung**  
 Stellt eine kurze Beschreibung der ausgewählten Business Intelligence-Erweiterung bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  