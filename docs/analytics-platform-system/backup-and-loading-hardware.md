---
title: 'Sichern #a0 Laden von Hardware'
description: Zum Bereitstellen Ihrer End-to-End-Data Warehousing-Lösung in Analytics Platform System (APS) mit Parallel Data Warehouse (PDW) müssen Sie einen Plan zum Sichern der Data Warehouse und zum Laden von Daten erstellen. Verwenden Sie diesen Leitfaden, um Sicherungs-und lade Server zu erwerben und zu konfigurieren, die Ihren Geschäftsanforderungen gerecht werden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4dd4fba91b1507f711a66a88f40b2fa2ea35e1ae
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401363"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>Übersicht über das Sichern und Laden von Hardware-parallel Data Warehouse
Zum Bereitstellen Ihrer End-to-End-Data Warehousing-Lösung in Analytics Platform System (APS) mit Parallel Data Warehouse (PDW) müssen Sie einen Plan zum Sichern der Data Warehouse und zum Laden von Daten erstellen. Verwenden Sie diesen Leitfaden, um Sicherungs-und lade Server zu erwerben und zu konfigurieren, die Ihren Geschäftsanforderungen gerecht werden.  
  
## <a name="acquire-and-configure-backup-servers"></a>Abrufen und Konfigurieren von Sicherungs Servern  
![Sicherungsprozess](media/backup-process.png "Sicherungsprozess")  
  
Zum Sichern einer PDW-Datenbank benötigen Sie mindestens einen Sicherungs Server. Sie können Ihre eigene vorhandene Hardware verwenden oder neue Hardware erwerben. Weitere Informationen finden Sie unter [erwerben und Konfigurieren eines Sicherungs Servers](acquire-and-configure-backup-server.md). Diese Anweisungen enthalten ein [Arbeitsblatt zur Kapazitätsplanung für Sicherungs Server](backup-capacity-planning-worksheet.md) , mit dem Sie die richtige Lösung für die Sicherung planen können.  
  
## <a name="acquire-and-configure-loading-servers"></a>Erwerben und Konfigurieren von Server Ladevorgängen  
![Ladevorgang](media/loading-process.png "Ladevorgang")  
  
Zum Laden von Daten benötigen Sie mindestens einen Lade Server. Sie können Ihre eigene vorhandene ETL-oder andere Server verwenden, oder Sie können neue Server erwerben. Weitere Informationen finden Sie unter [erwerben und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md). Diese Anweisungen enthalten ein [Arbeitsblatt zum Planen der Server Kapazitätsplanung](loading-server-capacity-planning-worksheet.md) , mit dem Sie die richtige Lösung für das Laden planen können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Übersicht über die Sicherung und Wiederherstellung](backup-and-restore-overview.md)  
[Übersicht laden](load-overview.md)  
  
