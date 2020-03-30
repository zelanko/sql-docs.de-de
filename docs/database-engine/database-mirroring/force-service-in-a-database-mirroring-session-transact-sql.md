---
title: Erzwungener Datenbankspiegelungsdienst
description: Wenn der Prinzipalserver ausfällt, während der Spiegelungsserver verfügbar ist, können Sie die Datenbank verfügbar machen, indem Sie ein Failover des Diensts auf die gespiegelte Datenbank (mit möglichem Datenverlust) erzwingen.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 970f399ab6227fdaf2672bf887c250b6be02de1e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74822220"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a>Erzwingen des Diensts in einer Datenbank-Spiegelungssitzung (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn der Prinzipalserver im Modus für hohe Leistung und im Modus für hohe Sicherheit ohne automatisches Failover ausfällt, der Spiegelserver jedoch zur Verfügung steht, kann der Datenbankbesitzer die Datenbank verfügbar machen, indem er ein Failover des Diensts auf die Spiegeldatenbank (bei möglichem Datenverlust) erzwingt. Diese Option steht nur zur Verfügung, wenn alle der folgenden Bedingungen erfüllt sind:  
  
-   Der Prinzipalserver ist ausgefallen.  
  
-   WITNESS ist auf OFF festgelegt oder ist mit dem Spiegelserver verbunden.  
  
> [!CAUTION]  
>  Das Erzwingen des Diensts ist eine Methode, die ausschließlich der Wiederherstellung in einem Notfall dient. Das Erzwingen des Diensts kann Datenverluste zur Folge haben. Sie sollten den Dienst daher nur erzwingen, wenn Sie bereit sind, Datenverluste in Kauf zu nehmen, um den Dienst für die Datenbank unverzüglich wiederherzustellen. Wenn es beim Erzwingen des Diensts zum Verlust wichtiger Daten kommen kann, wird empfohlen, die Spiegelung zu beenden und die Datenbanken manuell neu zu synchronisieren. Weitere Informationen zu den Risiken beim Erzwingen des Diensts finden Sie unter [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md).  
  
 Durch das Erzwingen des Diensts wird die Sitzung angehalten und ein neuer Wiederherstellungszweig gestartet. Die Auswirkungen aus dem Erzwingen des Diensts sind vergleichbar mit dem Entfernen der Spiegelung und dem Wiederherstellen der vorherigen Prinzipaldatenbank. Durch das Erzwingen des Diensts wird jedoch das erneute Synchronisieren der Datenbanken (bei möglichem Datenverlust) vereinfacht, wenn die Spiegelung fortgesetzt wird.  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a>So erzwingen Sie den Dienst in einer Datenbank-Spiegelungssitzung  
  
1.  Stellen Sie eine Verbindung zum Spiegelserver her.  
  
2.  Führen Sie die folgende Anweisung aus:  
  
     ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS  
  
     Dabei ist *<database_name>* die gespiegelte Datenbank.  
  
     Der Spiegelserver wird unverzüglich zum Prinzipalserver, und die Spiegelung wird unterbrochen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
