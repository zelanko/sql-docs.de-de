---
title: MSSQLSERVER_5243 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5243 (Database Engine error)
ms.assetid: e04a1934-e57d-420e-ac79-97071745824e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f6176b0e0f7c179c9817a65bb20d6370d83b2c23
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717019"
---
# <a name="mssqlserver_5243"></a>MSSQLSERVER_5243
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|5243|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Während eines internen Vorgangs wurde eine Inkonsistenz gefunden. Wenden Sie sich an den technischen Support. Referenznummer %ld.|  
  
## <a name="explanation"></a>Erklärung  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde eine strukturelle Inkonsistenz in einer speicherinternen Speicher-Engine-Struktur erkannt.  
  
## <a name="user-action"></a>Benutzeraktion  
Hardwarefehlersuche Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Prüfen Sie zudem die Windows-System- und -Anwendungsprotokolle sowie das SQL Server-Fehlerprotokoll, um anzuzeigen, ob der Fehler in Folge eines Hardwarefehlers aufgetreten ist. Beheben Sie alle durch die Hardware bedingten Probleme, die in den Protokollen enthalten sind.

Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.

Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.

Wiederherstellen aus einer Sicherung. Stellen Sie die Datenbank von der Sicherung wieder her, wenn das Problem nicht durch die Hardware bedingt und eine fehlerfreie Sicherung verfügbar ist.

Ausführen von DBCC CHECKDB. Führen Sie DBCC CHECKDB ohne eine REPAIR-Klausel aus, um das Ausmaß der Beschädigung festzustellen, falls keine fehlerfreie Sicherung verfügbar ist. DBCC CHECKDB empfiehlt die Verwendung einer REPAIR-Klausel. Führen Sie dann DBCC CHECKDB mit der entsprechenden REPAIR-Klausel aus, um die Beschädigung zu reparieren.

> **ALERT-Tag wird nicht unterstützt!!!!** 
> **TR-Tag wird nicht unterstützt!!!!** 
> **TR-Tag wird nicht unterstützt!!!!**

Wenn DBCC CHECKDB mit einer der REPAIR-Klauseln ausgeführt wird und das Problem nicht behebt, wenden Sie sich an Ihren primären Unterstützungsanbieter.
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Datenbankdateien und Dateigruppen](~/relational-databases/databases/database-files-and-filegroups.md)  
  
