---
title: MSSQLSERVER_9955 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9713e90fa15683fe4af619c66c9714c18c405cd5
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553005"
---
# <a name="mssqlserver_9955"></a>MSSQLSERVER_9955
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9955|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FTXT2_MSSEARCHACCESSDENY|  
|Meldungstext|SQL Server konnte die Named Pipe '%ls' zur Kommunikation mit dem Volltextfilterdaemon nicht erstellen (Windows-Fehler: %d). Entweder ist bereits eine Named Pipe für einen Filterdaemon-Hostprozess vorhanden oder die Systemressourcen reichen nicht aus oder bei der Suche nach der Sicherheits-ID (SID) für die Kontogruppe des Filterdaemons ist ein Fehler aufgetreten. Um diesen Fehler zu beheben, müssen Sie alle laufenden Prozesse des Volltextfilterdaemons beenden und ggf. das Dienstkonto des Volltextdaemon-Startprogramms neu konfigurieren.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung wird angezeigt, weil [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Named Pipe zur Kommunikation mit dem Volltextfilterdaemon nicht erstellen konnte. Entweder ist bereits eine Named Pipe für einen Filterdaemon-Hostprozess vorhanden oder die Systemressourcen reichen nicht aus oder bei der Suche nach der Sicherheits-ID (SID) für die Kontogruppe des Filterdaemons ist ein Fehler aufgetreten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Um diesen Fehler zu beheben, müssen Sie alle laufenden Prozesse des Volltextfilterdaemons beenden und ggf. das Hostkonto des Volltextfilterdaemons mit dem SQL Server-Konfigurations-Manager neu konfigurieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md)   
 [Festlegen des Dienst Kontos für das Start Programm des Volltextfilterdaemons](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Volltextsuche](../search/full-text-search.md)  
  
  
