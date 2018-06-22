---
title: MSSQLSERVER_7907 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7907 (Database Engine error)
ms.assetid: a1c94e4a-7e91-46e0-9fac-07bbbf6dd018
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 007ce33742cb2d625b331992ae2b9edf39927ad0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149681"
---
# <a name="mssqlserver7907"></a>MSSQLSERVER_7907
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7907|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_FS_INVALID_COLUMN_DIRECTORY|  
|Meldungstext|Tabellenfehler: Das Verzeichnis 'DIRECTORY' in Partitions-ID PN_ID stellt kein gültiges Filestream-Verzeichnis dar.|  
  
## <a name="explanation"></a>Erklärung  
 Der Name eines Spaltenverzeichnisses stellt die Spalten-ID der Partition der relationalen Engine dar. Wenn ein Spaltenverzeichnisname nicht in eine Spalten-ID konvertiert werden kann, stellt das Verzeichnis kein gültiges Spaltenverzeichnis dar.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht verfügbar. Dieser Fehler kann nicht repariert werden. Wenn Sie die Datenbank nicht mithilfe einer Sicherung wiederherstellen können, wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  