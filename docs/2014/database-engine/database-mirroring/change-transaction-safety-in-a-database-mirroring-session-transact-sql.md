---
title: Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d1d3fa972c60ae68c835a9e27da67d0ab970f372
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148903"
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
  
     Dabei ist *\<database>* der Name der gespiegelten Datenbank.  
  
### <a name="to-turn-off-transaction-safety"></a>So deaktivieren Sie die Transaktionssicherheit  
  
1.  Stellen Sie eine Verbindung mit dem Prinzipalserver her.  
  
2.  Führen Sie die folgende Anweisung aus:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     Dabei ist *\<database>* die gespiegelte Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE-Datenbankspiegelung &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)  
  
  
