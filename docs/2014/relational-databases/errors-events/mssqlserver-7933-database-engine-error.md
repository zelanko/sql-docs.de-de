---
title: MSSQLSERVER_7933 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7933 (Database Engine error)
ms.assetid: 722bd2c6-0fb9-4838-954a-439744c6ac4b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be3d21665d41fe7748e6a3a4d070f4001ca306a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762036"
---
# <a name="mssqlserver7933"></a>MSSQLSERVER_7933
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7933|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_FS_ORPHANED_ROWSET_DIRECTORY|  
|Meldungstext|Tabellenfehler: Ein Filestream-Verzeichnis, die ID F_ID für eine Partition, aber die entsprechende Partition vorhanden ist, ist in der Datenbank nicht vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
 Während DBCC CHECKDB wurde ein Rowsetverzeichnis im FILESTREAM-Datenspeicher gefunden; die entsprechende Partition ist jedoch in der Datenbank nicht vorhanden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht verfügbar. Dieser Fehler kann nicht automatisch repariert werden. Wenn Sie die Datenbank nicht mithilfe einer Sicherung wiederherstellen können, wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
