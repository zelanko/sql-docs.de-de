---
title: MSSQLSERVER_9955 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7b77ea2e16a65d1fc93bc7199a8006c5e240561
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640098"
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9955|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FTXT2_MSSEARCHACCESSDENY|  
|Meldungstext|SQL Server konnte die Named Pipe '%ls' zur Kommunikation mit dem Volltextfilterdaemon nicht erstellen (Windows-Fehler: %d). Entweder ist bereits eine Named Pipe für einen Filterdaemon-Hostprozess vorhanden oder die Systemressourcen reichen nicht aus oder bei der Suche nach der Sicherheits-ID (SID) für die Kontogruppe des Filterdaemons ist ein Fehler aufgetreten. Um diesen Fehler zu beheben, müssen Sie alle laufenden Prozesse des Volltextfilterdaemons beenden und ggf. das Dienstkonto des Volltextdaemon-Startprogramms neu konfigurieren.|  
  
## <a name="explanation"></a>Erklärung  
Diese Meldung wird angezeigt, weil [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Named Pipe zur Kommunikation mit dem Volltextfilterdaemon nicht erstellen konnte. Entweder ist bereits eine Named Pipe für einen Filterdaemon-Hostprozess vorhanden oder die Systemressourcen reichen nicht aus oder bei der Suche nach der Sicherheits-ID (SID) für die Kontogruppe des Filterdaemons ist ein Fehler aufgetreten.  
  
## <a name="user-action"></a>Benutzeraktion  
Um diesen Fehler zu beheben, müssen Sie alle laufenden Prozesse des Volltextfilterdaemons beenden und ggf. das Hostkonto des Volltextfilterdaemons mit dem SQL Server-Konfigurations-Manager neu konfigurieren.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[SQL Server-Konfigurations-Manager](~/relational-databases/sql-server-configuration-manager.md)  
[Festlegen des Dienstkontos für das Startprogramm des Volltextfilterdaemon](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Volltextsuche](~/relational-databases/search/full-text-search.md)  
  
