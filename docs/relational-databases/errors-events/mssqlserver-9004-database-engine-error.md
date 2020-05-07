---
title: MSSQLSERVER_9004 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9593cfdc08161d3352c59332970aee668a89f4f0
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81727947"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9004|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_CORRUPT|  
|Meldungstext|Fehler beim Verarbeiten des Protokolls für die '%.*ls'-Datenbank.  Führen Sie nach Möglichkeit eine Wiederherstellung von einer Sicherung aus. Falls keine Sicherung verfügbar ist, muss das Protokoll möglicherweise neu erstellt werden.|  
  
## <a name="explanation"></a>Erklärung  
Bei der Verarbeitung des Protokolls während eines Rollbacks, einer Wiederherstellung oder Replikation ist ein Fehler aufgetreten. Dabei kann es sich um einen vom Betriebssystem erkannten Fehler oder um einen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkannten internen Konsistenzfehler handeln.  
Der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] führt logische Konsistenzprüfungen der Inhalte des Transaktionsprotokolls durch, während er sie liest und verarbeitet. Nicht alle Aspekte von Protokollheader, Protokollblöcken und Protokolldatensätzen werden geprüft. Die Statusnummer stellt weitere Informationen zur Art des Fehlers zur Verfügung:

 - **Status 1** Der Protokolldateiheader der virtuellen Protokolldatei (VIrtual Log File, VLF) wurde beschädigt.  Wenn im Rahmen des Startens der Datenbank beim Dienststart ein beschädigter Protokolldateiheader erkannt wird, wird im ERRORLOG möglicherweise nur Fehler 9004 verzeichnet. Der Protokolldateiheader ist der erste Teil jeder VLF innerhalb eines Transaktionsprotokolls. Der Protokolldateiheader ist nicht mit dem Einzeldateiheader, den ersten 8 KB der Protokolldatei, zu verwechseln. Wenn der Dateiheader beschädigt ist, empfangen Sie möglicherweise Msg 5172, ähnlich wie bei einer beschädigten Headerseite einer Datenbankdatei.
 - **Status 2 und 3** Beim Durchführen der Wiederherstellung während eines RESTORE-Vorgangs wurde ein ungültiger Protokollblock gefunden.
 - **Status 4 bis 12** Diese sind alle Überprüfungen von Protokollblöcken beim Verarbeiten von Protokolldatensätzen. Dazu zählen Parität, Sektor und andere logische Prüfungen der Konsistenz des Transaktionsprotokolls

In den meisten Fällen tritt dieser Fehler nur im ERRORLOG oder im Windows-Anwendungsereignisprotokoll mit EventID = 9004 auf, da der Vorgang zur Bearbeitung des Protokolls nicht auf einem direkten Benutzerbefehl basiert (wie etwa die Wiederherstellung, die beim Starten der SQL Server-Engine ausgeführt wird). In diesen Situationen tritt Fehler 9004 häufig zusammen mit Fehler 3414 auf. Einige Abfragen, wie etwa ALTER DATABASE, können jedoch eine Verarbeitung des Protokolls erforderlich machen und daher zu diesen Fehlern führen. Da der Fehler den Schweregrad=21 aufweist, wird die Benutzersitzung getrennt.

## <a name="cause"></a>Ursache
Fehler 9004 ist ein allgemeiner Fehler, der darauf hinweist, dass die Inhalte des Transaktionsprotokolls beschädigt sind. Der Grund, warum das Protokoll inkonsistent wird, ist den Gründen jedes Beschädigungsproblems von Datenbanken ähnlich, die von der SQL Server-Engine erkannt werden. Um die Ursache für die Beschädigung des Protokolls zu finden, sollten Sie ähnliche Techniken wie für beschädigte Datenbanken einsetzen, einschließlich einer Analyse möglicher Probleme bei Hardware, Dateisystem und E/A. Beachten Sie, dass DBCC CHECKDB das Transaktionsprotokoll im Rahmen seiner Ausführung nicht überprüft und Beschädigungsfehler in Protokollen nicht erkennen kann. Fehler 9004 wird von der SQL Server-Engine selbst ausgelöst.

## <a name="user-action"></a>Benutzeraktion  
Durch eine der folgenden Aktionen wird dieser Fehler korrigiert:  
  
-   **Wiederherstellen einer Sicherung**:  Führen Sie eine Wiederherstellung aus einer als fehlerfrei bekannten Sicherung durch, um eine Wiederherstellung nach diesem Problem zu erreichen. Wenn der Protokollanteil einer Datenbank- oder Protokollsicherung beschädigte Inhalte enthält, tritt möglicherweise beim RESTORE ein Fehler 9004 auf. In dieser Situation ist das Transaktionsprotokoll in der Sicherung beschädigt.
  
-   **Erneutes Erstellen des Protokolls**:  Wenn Sie keine Wiederherstellung aus einer Sicherung ausführen können, gelingt es Ihnen möglicherweise, die Datenbank in den Onlinemodus zu versetzen, indem Sie das Transaktionsprotokoll neu erstellen. Sie sollten sich um ein detailliertes Verständnis der Auswirkungen bemühen, die eine Neuerstellung des Transaktionsprotokolls haben kann. Dies schließt den *möglichen Verlust der Transaktionskonsistenz in der Datenbank* ein. Weitere Informationen zur Neuerstellung des Transaktionsprotokolls finden Sie unter [Beheben von Fehlern im Datenbank-Notfallmodus](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md#resolving-errors-in-database-emergency-mode).
  
-   **Untersuchen der Protokolle auf Systemprobleme**: Überprüfen Sie außerdem das Systemereignisprotokoll und die Fehlerprotokolle, um Probleme innerhalb des Systems zu identifizieren, die für den Fehler verantwortlich sein können.  
  
