---
title: XTP-Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96d60ae8fc176fc1fc108d907f33f01877795955
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805423"
---
# <a name="xtp-transactions"></a>XTP-Transaktionen
  Das XTP-Leistungsobjekt für Transaktionen enthält Leistungsindikatoren für XTP-Engine-Transaktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
 [XTP &#40;In-Memory-OLTP&#41; -Leistungsindikatoren](../../integration-services/performance/performance-counters.md)  
  
  
