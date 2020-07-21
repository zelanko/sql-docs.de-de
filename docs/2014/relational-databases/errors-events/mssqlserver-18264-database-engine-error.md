---
title: MSSQLSERVER_18264 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d32f3570237ea35a8c1e9c2ce99159fd7b1fcfaf
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552295"
---
# <a name="mssqlserver_18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
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
 [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
