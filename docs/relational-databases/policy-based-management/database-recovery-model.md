---
title: Datenbank-Wiederherstellungsmodell
description: Hier erfahren Sie, wie Sie eine Richtlinie aktivieren, mit der das Sicherungswiederherstellungsmodell für Benutzerdatenbanken überprüft wird, um Datenverlust zu verringern.
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
ms.openlocfilehash: 048fa8d28e32ad73aa9e2a85e217f268fa865a3c
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285072"
---
# <a name="database-recovery-model"></a>Datenbank-Wiederherstellungsmodell
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Für die SQL Server Enterprise und Standard überprüft diese Regel, ob für nicht schreibgeschützte Benutzerdatenbanken das einfache Wiederherstellungsmodell festgelegt ist. Für Produktionsdatenbanken empfiehlt sich die Verwendung des vollständigen Wiederherstellungsmodells anstelle des einfachen Wiederherstellungsmodells. Der vollständige Wiederherstellungsmodus ermöglicht die Zeitpunktwiederherstellung. Auf diese Weise können bei der Wiederherstellung im Notfall Datenverluste verringert werden.
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Produktionsdatenbanken sollten im vollständigen Wiederherstellungsmodus betrieben werden, und das Transaktionsprotokoll sollte häufig gesichert werden, um eine Wiederherstellbarkeit bei minimalen Datenverlusten sicherzustellen.
  
## <a name="see-also"></a>Weitere Informationen 
  
 [Übersicht über Wiederherstellungsvorgänge](../backup-restore/restore-and-recovery-overview-sql-server.md)   
  
 [Vollständige Datenbankwiederherstellungen (vollständiges Wiederherstellungsmodell)](../backup-restore/complete-database-restores-full-recovery-model.md)  

 [Transaktionsprotokollsicherungen](../backup-restore/transaction-log-backups-sql-server.md)   
  
