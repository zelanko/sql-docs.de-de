---
title: 'MSSQLSERVER: Datenbank-Engine-Fehler | Microsoft Dokumentation'
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ad9da93b21133817852efde492d10fed179fbcce
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58305878"
---
# <a name="mssqlserver---database-engine-error"></a>MSSQLSERVER: Datenbank-Engine-Fehler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|823|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|B_HARDERR|  
|Meldungstext|Das Betriebssystem hat während eines %S_MSG bei Offset %#016I64x in der Datei '%4!s!' den Fehler '%ls' an SQL Server zurückgegeben. Weitere Informationen finden Sie möglicherweise in zusätzlichen Meldungen im SQL Server-Fehlerprotokoll und im Systemereignisprotokoll. Dieser Fehler kann die Datenbankintegrität beeinträchtigen und muss behoben werden. Führen Sie eine vollständige Datenbankkonsistenzprüfung (DBCC CHECKDB) aus. Dieser Fehler kann viele Ursachen haben. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Fehler bei einer Lese- oder Schreibanforderung in Windows. Der von Windows zurückgegebene Fehlercode und der entsprechende Text werden in die Meldung eingefügt. Im Fall des Lesevorgangs hat [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereits viermal versucht, die Leseanforderung zu wiederholen. Dieser Fehler beruht oft auf einem Hardwarefehler, wird jedoch möglicherweise durch den Gerätetreiber verursacht. Weitere Informationen zu Fehlermeldung 823 finden Sie unter [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339). Weitere Informationen zu E/A-Fehlern finden Sie unter [Microsoft SQL Server I/O Basics, Chapter 2 (E/A-Grundlagen von Microsoft SQL Server, Kapitel 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie, ob zusätzliche Informationen im Systemereignisprotokoll vorhanden sind. Wenden Sie sich an den Hardwarehersteller oder an Microsoft Support Services, um Unterstützung bei der Bestimmung der Ursache zu erhalten und diese Ursache zu beheben. Nachdem der Hardwarefehler behoben wurde, stellen Sie alle Datenbanken wieder her, und führen Sie DBCC CHECKDB aus.  
  
