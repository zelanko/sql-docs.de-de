---
title: MSSQLSERVER_825 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 675333d22f1d3828831fbce6c444df1e89c89fe4
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306059"
---
# <a name="mssqlserver825"></a>MSSQLSERVER_825
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|825|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|B_RETRYWORKED|  
|Meldungstext|Ein Lesevorgang für die Datei '%ls' und den Offset %#016I64x war nach %d fehlerhaften Versuchen mit dem Fehler %ls erfolgreich. Weitere Informationen finden Sie möglicherweise in zusätzlichen Meldungen im SQL Server-Fehlerprotokoll und im Systemereignisprotokoll. Dieser Fehler bedroht die Datenbankintegrität und muss behoben werden. Führen Sie eine vollständige Datenbankkonsistenzprüfung (DBCC CHECKDB) aus. Dieser Fehler kann viele Ursachen haben. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Mit dieser Meldung wird angegeben, dass der Lesevorgang mindestens ein Mal wiederholt werden musste. Zudem wird hiermit auf ein größeres Problem mit der Datenträgerhardware hingewiesen. Diese Meldung deutet aktuell nicht auf ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Problem hin, durch das Datenträgerproblem werden möglicherweise Datenverluste oder Beschädigungen der Datenbank verursacht, wenn es nicht behoben wird. Das Systemereignisprotokoll enthält möglicherweise ähnliche Ereignisse, anhand derer eine Problemdiagnose vorgenommen werden kann. Weitere Informationen zu E/A-Fehlern finden Sie unter [Microsoft SQL Server I/O Basics, Chapter 2 (E/A-Grundlagen von Microsoft SQL Server, Kapitel 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  
  
## <a name="user-action"></a>Benutzeraktion  
Mit den folgenden Aktionen können Sie das zugrunde liegende Problem möglicherweise identifizieren und lösen:  
  
-   Beachten Sie das Fehlerprotokoll und den jeweiligen Text in dieser Meldung, um Informationen zu den Ursachen für das Problem zu erfahren.  
  
-   Prüfen Sie Ihr Datenträgersystem. Das Problem ist möglicherweise auf die Datenträger, Datenträgercontroller, Arraykarten oder Datenträgertreiber zurückzuführen.  
  
-   Die neuesten Hilfsprogramme zum Überprüfen des Status Ihres Datenträgersystems erhalten Sie beim Hersteller des Datenträgers.  
  
-   Wenden Sie sich an den Hersteller des Datenträgers, um die neuesten Treiberupdates zu erhalten.  
  
