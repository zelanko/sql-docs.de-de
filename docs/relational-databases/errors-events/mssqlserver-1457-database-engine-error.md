---
description: MSSQLSERVER_1457
title: MSSQLSERVER_1457 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9d9c797f1c7071518b79a7f90d4a99d312eda55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88334086"
---
# <a name="mssqlserver_1457"></a>MSSQLSERVER_1457
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|1457|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_PAGE_UNDO_PENDING|  
|Meldungstext|Die Synchronisierung der '%.*ls'-Spiegeldatenbank wurde unterbrochen, und die Datenbank weist nun einen inkonsistenten Status auf. Der ALTER DATABASE-Befehl ist fehlgeschlagen. Stellen Sie sicher, dass die Spiegeldatenbank wieder online ist. Stellen Sie dann erneut eine Verbindung mit der Spiegelserverinstanz her, und warten Sie, bis die Synchronisierung der Spiegeldatenbank beendet ist.|  
  
## <a name="explanation"></a>Erklärung  
Mit dieser Meldung wird angegeben, dass mit der ALTER DATABASE *Datenbank_Name* SET PARTNER OFF-Anweisung ein Fehler ausgelöst wurde. Durch den Fehler beim Versuch, die Datenbankspiegelung zu entfernen, wurde die Synchronisierung der Spiegeldatenbank unterbrochen. Die Datenbank weist nun einen inkonsistenten Status auf.  
  
## <a name="user-action"></a>Benutzeraktion  
So können Sie diesen Fehler mit einer der folgenden Aktionen beheben:  
  
-   Stellen Sie die Verbindung zwischen dem Spiegelserver und dem Prinzipalserver wieder her, um eine Synchronisierung der Spiegeldatenbank zu ermöglichen.  
  
-   Löschen Sie die Spiegeldatenbank.  
  
    Nach dem Löschvorgang können Sie aus den Sicherungen eine neue Spiegeldatenbank erstellen.  
  
    > [!NOTE]  
    > Solange die Spiegelung noch aktiviert ist, können Sie die Spiegeldatenbank nur nach einem Fehler bei der SET PARTNER OFF-Anweisung löschen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Datenbankspiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
[Entfernen der Datenbankspiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
[Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
