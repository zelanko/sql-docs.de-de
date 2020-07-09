---
title: MSSQLSERVER_18264 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3c37ae932acd8a1a2571d97a0564ffbfbe7037d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780642"
---
# <a name="mssqlserver_18264"></a>MSSQLSERVER_18264
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|Microsoft SQL Server|  
|Ereignis-ID|18264|  
|Ereignisquelle|MSSQLENGINE|  
|Komponente|SQLEngine|  
|Symbolischer Name|STRMIO_DBDUMP|  
|Meldungstext|Die Datenbank wurde gesichert. Datenbank: %s, Erstellungsdatum(-zeit): %s(%s), gesicherte Seiten: %d, Erste LSN: %s, Letzte LSN: %s, Anzahl der Sicherungsgeräte: %d, Geräteinformationen: (%s). Diese Meldung dient nur zu Informationszwecken. Es ist keine Benutzeraktion erforderlich.|  
  
## <a name="explanation"></a>Erklärung  
Standardmäßig wird diese Informationsmeldung bei jeder erfolgreichen Sicherung dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll und dem Systemereignisprotokoll hinzugefügt. Wenn Sie das Transaktionsprotokoll sehr häufig sichern, kann die Anzahl dieser Meldungen schnell ansteigen, d.h., es entstehen sehr große Fehlerprotokolle, die das Suchen nach anderen Meldungen erschweren können.  
  
## <a name="user-action"></a>Benutzeraktion  
Sie können diese Protokolleinträge mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ablaufverfolgungsflag **3226** unterdrücken. Es ist sehr hilfreich, dieses Ablaufverfolgungsflag zu aktivieren, wenn Sie regelmäßig Protokollsicherungen ausführen und keines der Skripts von diesen Einträgen abhängig ist.  
  
Weitere Informationen zum Verwenden von Ablaufverfolgungsflags finden Sie in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
[Ablaufverfolgungsflags &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  
