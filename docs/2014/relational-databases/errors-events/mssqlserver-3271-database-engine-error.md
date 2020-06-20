---
title: MSSQLSERVER_3271 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: de95b87cf7592ef3798a0fd58c9620042fa01f40
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033847"
---
# <a name="mssqlserver_3271"></a>MSSQLSERVER_3271
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3271|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DMPIO_IO_ERROR|  
|Meldungstext|Nicht behebbarer E/A-Fehler für die Datei "%ls:" %ls.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist ein allgemeiner Fehler, der auftritt, wenn das Betriebssystem beim Ausführen von E/A während eines Sicherungs- oder Wiederherstellungsvorgangs einen Fehler auslöst. In den meisten Situationen besteht die Ursache schlichtweg darin, dass das Sicherungsmedium voll ist.  
  
 Der Fehler enthält möglicherweise zusätzlichen Text vom Betriebssystem, der besagt, dass der Datenträger voll ist. Wenn Sie einen Sicherungs- oder Wiederherstellungsvorgang mit Sicherungssoftware eines Drittanbieters ausführen, wird möglicherweise eine zusätzliche Meldung ausgegeben, die besagt, dass bei der Sicherung ein Fehler erzeugt wurde. Die Meldung sieht möglicherweise wie der folgende Text aus:  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 Dies ist ein Hinweis darauf, dass die Sicherungssoftware eine Beendigung des Sicherungs- oder Wiederherstellungsvorgangs angefordert hat.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie die folgenden Tasks entsprechend aus:  
  
-   Überprüfen Sie die vorherigen zugrunde liegenden Systemfehlermeldungen und SQL Server-Fehlermeldungen, um die Ursache des Fehlers zu identifizieren.  
  
-   Stellen Sie sicher, dass das Sicherungs- und Wiederherstellungsmedium über genügend Speicherplatz verfügt.  
  
-   Beheben Sie alle Fehler, die von Sicherungs- und Wiederherstellungssoftware von Drittanbietern ausgelöst wurden.  
  
  
