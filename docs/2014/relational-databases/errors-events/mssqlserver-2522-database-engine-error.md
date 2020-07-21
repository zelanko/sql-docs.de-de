---
title: MSSQLSERVER_2522 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2522 (Database Engine error)
ms.assetid: 19b9b00c-330f-4dd3-9052-9d88bce83849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c789fb5017b8d64e450d424d4ffde7dd0db37dc5
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552105"
---
# <a name="mssqlserver_2522"></a>MSSQLSERVER_2522
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2522|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_INDEX_FILEGROUP_IS_INVALID|  
|Meldungstext|Der I_NAME-Index der O_NAME-Tabelle kann nicht verarbeitet werden, da die Dateigruppe F_NAME ungültig ist.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Informationsmeldung gibt an, dass der Index nicht überprüft werden kann, da eine der Dateigruppen-IDs, die in den Metadaten des Indexes gespeichert ist, nicht vorhanden ist. Die ungültige Dateigruppen-ID bezieht sich möglicherweise auf die Daten selbst, auf die LOB-Daten (Large Object) oder auf die Zeilenüberlaufdaten.  
  
 Wenn keine Probleme vorhanden sind, werden alle anderen Indizes des gleichen Objekts überprüft.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht zutreffend Dieser Fehler kann nicht automatisch repariert werden.  
  
  
