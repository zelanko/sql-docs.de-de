---
title: MSSQLSERVER_7935 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7935 (Database Engine error)
ms.assetid: 45ab21a3-024a-4523-9bd9-1175d01f9c8a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9441a002f7c6e7113970bd4fb847f3371fd67909
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762055"
---
# <a name="mssqlserver7935"></a>MSSQLSERVER_7935
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7935|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_FS_MISSING_COLUMN|  
|Meldungstext|Tabellenfehler: Ein Filestream-Verzeichnis-ID F_ID für eine Spalte mit Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, aber diese Spalte vorhanden ist, ist in der Partition nicht vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
 Während DBCC CHECKDB wurde ein FILESTREAM-Verzeichnis für eine Spalte im angegebenen Objekt gefunden, die Spalte wurde jedoch nicht in den entsprechenden Metadaten der Partition gefunden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht verfügbar. Dieser Fehler kann nicht automatisch repariert werden. Wenn Sie die Datenbank nicht mithilfe einer Sicherung wiederherstellen können, wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
