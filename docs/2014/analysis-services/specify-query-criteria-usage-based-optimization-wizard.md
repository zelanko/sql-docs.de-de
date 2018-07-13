---
title: Angeben von Abfragekriterien (Verwendungsbasierte Optimierung-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 46a0877a1f51964287f9a01f00adeae23d2dcfd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176427"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a>Abfragekriterien angeben (Assistent für verwendungsbasierte Optimierung)
  Über die Seite **Abfragekriterien festlegen** können Sie ein oder mehrere Filteroptionen auswählen, um zu optimierende Abfragen zu identifizieren.  
  
> [!NOTE]  
>  Diese Seite ist deaktiviert, wenn [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] keine Verbindung mit dem Abfrageprotokoll herstellen kann.  
  
## <a name="options"></a>Tastatur  
 **Abfrageprotokollstatistik**  
 Zeigt Informationen zu den Abfragen an, die in dem Abfrageprotokoll für die ausgewählten Partitionen gespeichert sind. Folgende Elemente werden angezeigt:  
  
|Begriff|Definition|  
|----------|----------------|  
|**Abfragen gesamt**|Zeigt Informationen zur Gesamtzahl der Abfragen an, die in dem Abfrageprotokoll für die ausgewählten Partitionen gespeichert sind.|  
|**Unterschiedliche Abfragen**|Zeigt Informationen zur Gesamtzahl der unterschiedlichen Abfragen an, die in dem Abfrageprotokoll für die ausgewählten Partitionen gespeichert sind.|  
|**Unterschiedliche Benutzer**|Zeigt Informationen zur Gesamtzahl der unterschiedlichen Benutzer an, die Abfragen zugeordnet sind, die in dem Abfrageprotokoll für die ausgewählten Partitionen gespeichert sind.|  
|**Durchschnittliche Antwortzeit**|Zeigt Informationen zur durchschnittlichen Antwortzeit für Abfragen an, die in dem Abfrageprotokoll für die ausgewählten Partitionen gespeichert sind.|  
  
 **Startdatum**  
 Filtert Abfragen im Abfrageprotokoll auf der Grundlage eines Startdatums und einer Startzeit. Wählen Sie ein Datum aus der Dropdownliste aus, oder geben Sie ein Datum ein.  
  
> [!NOTE]  
>  Wenn die Option **Enddatum** nicht ausgewählt ist, werden alle Abfragen im Abfrageprotokoll einbezogen, die am oder nach dem für diese Option angegebenen Datum protokolliert wurden.  
  
 **Enddatum**  
 Filtert Abfragen im Abfrageprotokoll auf der Grundlage eines Enddatums und einer Beendigungszeit. Wählen Sie ein Datum aus der Dropdownliste aus, oder geben Sie ein Datum ein.  
  
> [!NOTE]  
>  Wenn die Option **Startdatum** nicht ausgewählt ist, werden alle Abfragen im Abfrageprotokoll einbezogen, die am oder vor dem für diese Option angegebenen Datum protokolliert wurden.  
  
 **Benutzer**  
 Filtert Abfragen im Abfrageprotokoll auf der Grundlage einer angegebenen Gruppe von Benutzern. Klicken Sie auf die Auslassungspunkte (**...**), um das Dialogfeld **Benutzerauswahl** anzuzeigen und Benutzer auszuwählen, nach denen die Abfragen gefiltert werden sollen. Weitere Informationen zum Dialogfeld **Benutzerauswahl** finden Sie unter [Dialogfeld „Benutzerauswahl“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Häufigste Abfragen**  
 Filtert die Abfragen im Abfrageprotokoll auf der Grundlage des höchsten Prozentanteils der am meisten ausgeführten unterschiedlichen Abfragen für die ausgewählten Partitionen. Wählen Sie einen Prozentwert im Textfeld aus, oder geben Sie einen Wert ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwendungsbasierte Optimierung-Assistent F1-Hilfe](usage-based-optimization-wizard-f1-help.md)   
 [Analysis Services-Assistenten &#40;mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
