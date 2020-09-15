---
title: Sicherungsdateien und Datenbankdateien müssen auf separaten Geräten gespeichert sein
description: Hier erfahren Sie, wie Sie eine Richtlinie aktivieren, um den Speicherort der Sicherungsdatei mit dem Speicherort der Datenbankdatei für die richtlinienbasierte Verwaltung mit SQL Server zu vergleichen.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 5b98f8163a3564ccc4aadac6c71c30eb5cf37697
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285066"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Sicherungsdateien und Datenbankdateien müssen auf separaten Geräten gespeichert sein
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob Datenbankdateien und Sicherungsdateien auf separaten Medien gespeichert sind. Wenn sich Datenbankdateien und Sicherungsdateien auf demselben Medium befinden und ein Fehler auftritt, stehen die Datenbank und die Sicherungen nicht mehr zur Verfügung. Wenn Sie die Daten und die Sicherungen auf separaten Medien speichern, wird auch die E/A-Leistung für die produktive Nutzung der Datenbank sowie für das Schreiben von Sicherungen optimiert.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Als Sicherungsdatenträger sollte ein anderer Datenträger als für die Datenbankdaten und Protokolldatenträger verwendet werden. Nur so kann sichergestellt werden, dass Sie auch dann auf die Sicherungen zugreifen können, wenn die Daten- oder Protokolldatenträger ausfallen.

Wenn sich Datenbankdateien und Sicherungsdateien auf demselben Medium befinden und ein Fehler auftritt, stehen die Datenbank und die Sicherungen nicht mehr zur Verfügung. Wenn Sie die Daten und die Sicherungen auf separaten Medien speichern, wird auch die E/A-Leistung für die produktive Nutzung der Datenbank sowie für das Schreiben von Sicherungen optimiert.
  
## <a name="see-also"></a>Weitere Informationen 
   
  
 [Sicherungsmedien](../backup-restore/backup-devices-sql-server.md)  
  
