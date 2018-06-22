---
title: XTP-Transaktionen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6b890ec229755db9c6ee9b292bf632d110e9c189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058476"
---
# <a name="xtp-transactions"></a>XTP-Transaktionen
  Das Leistungsobjekt "XTP-Transaktionen" enthält Leistungsindikatoren für XTP-Engine-Transaktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Diese Tabelle beschreibt die **XTP-Transaktionen** Leistungsindikatoren.  
  
|Leistungsindikator|Description|  
|-------------|-----------------|  
|**Abbruchweitergaben/s**|Die durchschnittliche Anzahl der Transaktionen, für die pro Sekunde aufgrund eines Commitabhängigkeits-Rollbacks ein Rollback durchgeführt wurde.|  
|**Übernommene Commitabhängigkeiten/s**|Die durchschnittliche Anzahl der Commitabhängigkeiten, die pro Sekunde von Transaktionen übernommen werden.|  
|**Vorbereitete schreibgeschützte Transaktionen/s**|Die Anzahl der schreibgeschützten Transaktionen, die pro Sekunde für die Commitverarbeitung vorbereitet wurden.|  
|**Sicherungspunktaktualisierungen/s**|Die durchschnittliche Häufigkeit pro Sekunde, mit der ein Sicherungspunkt aktualisiert wurde. Eine Sicherungspunktaktualisierung erfolgt, wenn ein vorhandener Sicherungspunkt auf den aktuellen Punkt in der Lebensdauer der Transaktion zurückgesetzt wird.|  
|**Sicherungspunkt-Rollbacks/s**|Die durchschnittliche Häufigkeit, mit der für eine Transaktion pro Sekunde ein Rollback auf einen Sicherungspunkt ausgeführt wurde.|  
|**Erstellte Sicherungspunkte/s**|Die durchschnittliche Anzahl der pro Sekunde erstellten Sicherungspunkte.|  
|**Transaktionsüberprüfungsfehler/s**|Die durchschnittliche Anzahl der Transaktionen mit fehlgeschlagener Überprüfungsverarbeitung (pro Sekunde).|  
|**Vom Benutzer abgebrochene Transaktionen/s**|Die durchschnittliche Anzahl der Transaktionen, die pro Sekunde vom Benutzer abgebrochen wurden.|  
|**Abgebrochene Transaktionen/s**|Die durchschnittliche Anzahl der Transaktionen, die pro Sekunde vom Benutzer und vom System abgebrochen wurden.|  
|**Erstellte Transaktionen/s**|Die durchschnittliche Anzahl der pro Sekunde im System erstellten Transaktionen.<br /><br /> XTP-Transaktionen werden anders als datenträgerbasierte Transaktionen gezählt (wie aus Datenbanken:Transaktionen/Sekunde ersichtlich). Beispielsweise zählt Erstellte Transaktionen/s schreibgeschützte Transaktionen, Datenbanken:Transaktionen/Sekunde hingegen nicht.|  
  
## <a name="see-also"></a>Siehe auch  
 [XTP &#40;In-Memory OLTP&#41; -Leistungsindikatoren](../../integration-services/performance/performance-counters.md)  
  
  