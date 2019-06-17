---
title: MSSQLSERVER_2534 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ed3a5a48a4c327decc75e37142c77d7d4ee52f1d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914656"
---
# <a name="mssqlserver2534"></a>MSSQLSERVER_2534
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2534|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT|  
|Meldungstext|Tabellenfehler: Page P_ID, laut Header gibt an, wie der Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, zugeordnet wird zuordnungseinheits-ID A_ID (Typ TYPE), wird von einem anderen Objekt zugeordnet.|  
  
## <a name="explanation"></a>Erklärung  
 Der Header der Seite enthält die Zuordnungseinheits-ID *A_ID*. Die Seite wird jedoch von keiner der IAM-Seiten (Index Allocation Map) dieser Zuordnungseinheit zugeordnet. Deshalb enthält der Header der Seite die falsche Zuordnungseinheits-ID, und die Seite verfügt über einen übereinstimmenden MSSQLServer_2533-Fehler, der der Zuordnungseinheits-ID entspricht, der die Seite tatsächlich zugeordnet ist.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Führen Sie DBCC CHECKDB ohne eine REPAIR-Klausel aus, um das Ausmaß der Beschädigung festzustellen, falls keine fehlerfreie Sicherung verfügbar ist. DBCC CHECKDB empfiehlt die Verwendung einer REPAIR-Klausel. Führen Sie dann DBCC CHECKDB mit der entsprechenden REPAIR-Klausel aus, um die Beschädigung zu reparieren.  
  
> [!CAUTION]  
>  Wenden Sie sich an Ihren primären Unterstützungsanbieter, bevor Sie diese Anweisung ausführen, wenn Sie nicht sicher sind, inwiefern sich die Verwendung von DBCC CHECKDB mit einer REPAIR-Klausel auf Ihre Daten auswirkt.  
  
 Wenn DBCC CHECKDB mit einer der REPAIR-Klauseln ausgeführt wird und das Problem nicht behebt, wenden Sie sich an Ihren primären Unterstützungsanbieter.  
  
### <a name="results-of-running-repair-options"></a>Ergebnis der Ausführung von REPAIR-Optionen  
 REPAIR erstellt den Index neu, wenn ein Index vorhanden ist.  
  
> [!CAUTION]  
>  Durch das Ausführen von REPAIR für den übereinstimmenden [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md)-Fehler wird die Zuordnung der Seite vor dem erneuten Build aufgehoben.  
  
> [!CAUTION]  
>  Diese Reparatur führt möglicherweise zum Datenverlust.  
  
  
