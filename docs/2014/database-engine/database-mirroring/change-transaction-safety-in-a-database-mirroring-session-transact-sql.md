---
title: Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934394"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung (Transact-SQL)
  Die Transaktionssicherheit ist das Attribut, das den Betriebsmodus der Sitzung steuert. Der Datenbankbesitzer kann die Transaktionssicherheit jedoch jederzeit ändern. Standardmäßig ist die Sicherheitsstufe für Transaktionen auf FULL (synchroner Betriebsmodus) festgelegt.  
  
 Wird die Transaktionssicherheit deaktiviert, geht die Sitzung in den asynchronen Betriebsmodus über, in dem die Leistung maximiert wird. Falls der Prinzipal nicht mehr verfügbar ist, wird der Spiegel beendet, ist jedoch als betriebsbereit verfügbar (ein Failover erfordert das Erzwingen des Diensts bei möglichem Datenverlust).  
  
### <a name="to-turn-on-transaction-safety"></a>So aktivieren Sie die Transaktionssicherheit  
  
1.  Stellen Sie eine Verbindung mit dem Prinzipalserver her.  
  
2.  Führen Sie die folgende Transact-SQL-Anweisung aus:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     dabei *\<database>* ist der Name der gespiegelten Datenbank.  
  
### <a name="to-turn-off-transaction-safety"></a>So deaktivieren Sie die Transaktionssicherheit  
  
1.  Stellen Sie eine Verbindung mit dem Prinzipalserver her.  
  
2.  Führen Sie die folgende Anweisung aus:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     dabei *\<database>* ist die gespiegelte Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Alter Database-Daten Bank Spiegelung &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Betriebsmodi der Datenbankspiegelung](database-mirroring-operating-modes.md)  
  
  
