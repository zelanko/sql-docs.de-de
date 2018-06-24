---
title: MSSQLSERVER_823 | Microsoft Docs
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
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a3889444fb2c605bccd36d30dbe324f220bbe942
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048980"
---
# <a name="mssqlserver823"></a>MSSQLSERVER_823
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|823|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|B_HARDERR|  
|Meldungstext|Das Betriebssystem hat während eines %S_MSG bei Offset %#016I64x in der Datei '%4!s!' den Fehler '%ls' an SQL Server zurückgegeben. Weitere Informationen finden Sie möglicherweise in zusätzlichen Meldungen im SQL Server-Fehlerprotokoll und im Systemereignisprotokoll. Dieser Fehler kann die Datenbankintegrität beeinträchtigen und muss behoben werden. Führen Sie eine vollständige Datenbankkonsistenzprüfung (DBCC CHECKDB) aus. Dieser Fehler kann viele Ursachen haben. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
 Fehler bei einer Lese- oder Schreibanforderung in Windows. Der von Windows zurückgegebene Fehlercode und der entsprechende Text werden in die Meldung eingefügt. Im Fall des Lesevorgangs hat [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereits viermal versucht, die Leseanforderung zu wiederholen. Dieser Fehler beruht oft auf einem Hardwarefehler, wird jedoch möglicherweise durch den Gerätetreiber verursacht. Weitere Informationen zu Fehlermeldung 823 finden Sie unter [http://support.microsoft.com/kb/828339](http://support.microsoft.com/kb/828339). Weitere Informationen zu E/A-Fehlern finden Sie unter [Microsoft SQL Server I/O Basics, Chapter 2 (E/A-Grundlagen von Microsoft SQL Server, Kapitel 2)](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie, ob zusätzliche Informationen im Systemereignisprotokoll vorhanden sind. Wenden Sie sich an den Hardwarehersteller oder an Microsoft Support Services, um Unterstützung bei der Bestimmung der Ursache zu erhalten und diese Ursache zu beheben. Nachdem der Hardwarefehler behoben wurde, stellen Sie alle Datenbanken wieder her, und führen Sie DBCC CHECKDB aus.  
  
  