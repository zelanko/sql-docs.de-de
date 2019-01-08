---
title: MSSQLSERVER_3168 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5ea24081f4b3a41211f3bd8d6bba52aaec8b74fc
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53370182"
---
# <a name="mssqlserver3168"></a>MSSQLSERVER_3168
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|3168|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_SYSTEMWRONGVER|  
|Meldungstext|Die Sicherung der Systemdatenbank auf dem Medium %ls kann nicht wiederhergestellt werden, da sie im Vergleich zu dieser Version des Servers (%ls) mit einer anderen Version (%ls) erstellt wurde.|  
  
## <a name="explanation"></a>Erklärung  
 Sie können eine Sicherung einer Systemdatenbank (**master**, **model** oder **msdb**) nicht auf einem Serverbuild wiederherstellen, der sich von dem Build unterscheidet, auf dem die Sicherung ursprünglich vorgenommen wurde.  
  
> [!NOTE]  
>  Durch die Installation eines Service Packs oder eines Hotfixbuilds ändert sich die Serverbuildnummer, und Serverbuilds sind stets inkrementell.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Das Datenbankschema für Systemdatenbanken kann serverbuildübergreifend geändert werden. Damit sichergestellt wird, dass eine Schemaänderung keine Inkonsistenzen verursacht, wird mit der RESTORE-Anweisung die Serverbuildnummer für die Sicherungsdatei mit der Buildnummer des Servers verglichen, auf dem Sie die Sicherung wiederherstellen möchten. Wenn sich die Builds unterscheiden, wird mit der Anweisung die Fehlermeldung 3168 ausgegeben, und der Wiederherstellungsvorgang wird fehlerbedingt beendet.  
  
 Im Folgenden werden Szenarien angegeben, in denen dieses Problem auftreten kann:  
  
-   Ein Benutzer versucht, eine Systemdatenbank auf Server A aus einer Sicherung wiederherzustellen, die auf Server B vorgenommen wurde. Server A und Server B befinden sich auf verschiedenen Serverbuilds. Server A könnte sich beispielsweise auf der ursprünglichen Buildversion befinden und Server B auf einem Build mit Service Pack 1 (SP1).  
  
-   Ein Benutzer versucht, eine Systemdatenbank aus einer Sicherung wiederherzustellen, die auf demselben Server vorgenommen wurde. Auf dem Server wurde jedoch ein anderer Build ausgeführt, als die Sicherung vorgenommen wurde. Das heißt, der Server wurde aktualisiert, seitdem die Sicherung ausgeführt wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 Der Wiederherstellungsvorgang gestaltet sich in dieser Situation ziemlich kompliziert und wird nur als letzte Möglichkeit verwendet. Weitere Informationen finden Sie unter „[Sie können Sicherungen von Systemdatenbanken nicht auf einem anderen Build von SQL Server wiederherstellen](https://support.microsoft.com/kb/264474)“.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
  
