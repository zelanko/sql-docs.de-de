---
title: Sicherungsdateien müssen sich auf separaten Geräten aus den Datenbankdateien befinden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5eff9cb3139e1e1043f99ba63d11160b1010c27
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936145"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Sicherungsdateien und Datenbankdateien müssen auf separaten Medien gespeichert sein
  Diese Regel überprüft, ob Datenbankdateien und Sicherungsdateien auf separaten Medien gespeichert sind. Wenn sich Datenbankdateien und Sicherungsdateien auf demselben Medium befinden und ein Fehler auftritt, stehen die Datenbank und die Sicherungen nicht mehr zur Verfügung. Wenn Sie die Daten und die Sicherungen auf separaten Medien speichern, wird auch die E/A-Leistung für die produktive Nutzung der Datenbank sowie für das Schreiben von Sicherungen optimiert.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es empfiehlt sich dringend, Datenbank und Sicherungen auf separaten Sicherungsmedien zu speichern.  
  
> [!NOTE]  
>  Diese Richtlinie kann separate physische Geräte nicht durch Einbindungspunkte erkennen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sicherungsmedien &#40;SQL Server&#41;](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
