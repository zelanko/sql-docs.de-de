---
description: MSSQLSERVER_5235
title: MSSQLSERVER_5235 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9086a2ba077c776c0d36a6ab5e7e2cafc97a688f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470998"
---
# <a name="mssqlserver_5235"></a>MSSQLSERVER_5235
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|5235|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|Meldungstext|[EMERGENCY] DBCC DBCC_COMMAND_DETAILS wurde von USER_NAME ausgeführt, wurde jedoch fehlerbedingt mit dem Fehlerzustand ERROR_STATE beendet. Verstrichene Zeit: HOURS Stunden, MINUTES Minuten, SECONDS Sekunden.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist die Zusammenfassungsmeldung, die von DBCC an das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll ausgegeben wird, wenn während der Ausführung des Befehls eine unerwartete Beendigung auftritt. Mit dem Fehlerzustand, der in der Meldung angegeben wird, wird der Typ der unerwarteten Beendigung definiert.  
  
In der folgenden Tabelle werden die Fehlerzustände aufgeführt und definiert.  
  
|Fehlerzustand|Definition|  
|---------------|--------------|  
|Status 1|Die Anweisung wurde aufgrund einer schwerwiegenden Beschädigung der Metadaten beendet. Diese Meldung wird von mindestens einer Instanz des Fehlers 8930 begleitet.|  
|Status 2|Die Anweisung wurde aufgrund eines internen Überprüfungsfehlers beendet. Diese Meldung wird von mindestens einer Instanz des Fehlers 8967 begleitet.|  
|Status 3|Bei den grundlegenden Systemtabellenüberprüfungen der zentralen Speicher-Engine-Systemtabellen ist ein Fehler aufgetreten. Diese Meldung wird von mindestens einer Instanz des Fehlers [7984](../../relational-databases/errors-events/mssqlserver-7984-database-engine-error.md), 7985, [7986](~/relational-databases/errors-events/mssqlserver-7986-database-engine-error.md), [7987](~/relational-databases/errors-events/mssqlserver-7987-database-engine-error.md), oder [7988](~/relational-databases/errors-events/mssqlserver-7988-database-engine-error.md) begleitet.|  
|Status 4|Bei der DBCC-Reparatur im Notfallmodus ist ein Fehler aufgetreten, da die Datenbank nach der erneuten Erstellung des Transaktionsprotokolls nicht gestartet werden konnte. Diese Meldung wird von Fehler 7909 begleitet.|  
|Status 5|Während der Ausführung des Befehls ist ein Fehler bei der Assertion oder eine Zugriffsverletzung aufgetreten.|  
|Status 6|Ein unbekannter Fehler ist aufgetreten, durch den der DBCC-Befehl unerwartet beendet wurde.|  
|Status 7|Eine nicht ordnungsgemäße Beendigung aufgrund eines Fehlers auf dem Replikat (Always On).|  
  
## <a name="user-action"></a>Benutzeraktion  
In der folgenden Tabelle wird die Benutzeraktion angegeben, die für den angegebenen Fehlerzustand angemessen ist.  
  
|Fehlerzustand|Benutzeraktion|  
|---------------|---------------|  
|Status 1|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 2|Wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|Status 3|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 4|Nehmen Sie eine Wiederherstellung von einer Sicherung vor.|  
|Status 4|Wenden Sie sich an den Kundenservice und -support.|  
|Status 6|Führen Sie den Befehl erneut aus. Wenden Sie sich an den Kundenservice und -support, wenn das Problem weiterhin auftritt.|  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-transact-sql.md)  
  
