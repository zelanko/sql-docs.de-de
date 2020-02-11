---
title: Übersicht über Wiederherstellungsvorgänge (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring tables [SQL Server]
- backups [SQL Server], restore scenarios
- database backups [SQL Server], restore scenarios
- database restores [SQL Server]
- restoring [SQL Server]
- restores [SQL Server]
- table restores [SQL Server]
- restoring databases [SQL Server], about restoring databases
- database restores [SQL Server], scenarios
ms.assetid: e985c9a6-4230-4087-9fdb-de8571ba5a5f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 254b05afdaa08483117c07660630b3120527a3fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921012"
---
# <a name="restore-and-recovery-overview-sql-server"></a>Übersicht über Wiederherstellungsvorgänge (SQL Server)
  Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank nach einem Ausfall wiederherzustellen, muss ein Datenbankadministrator einen Satz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen im Rahmen einer logisch folgerichtigen und sinnvollen Wiederherstellungssequenz wiederherstellen. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -RESTORE WITH RECOVERY unterstützt folgendermaßen die Wiederherstellung von Daten aus Sicherungskopien einer ganzen Datenbank, einer Datendatei oder einer Datenseite:  
  
-   Datenbank ( *Vollständige Datenbankwiederherstellung*)  
  
     Die gesamte Datenbank wird wiederhergestellt. Während des Wiederherstellungsvorgangs ist die Datenbank offline.  
  
-   Datendatei ( *Dateiwiederherstellung*)  
  
     Mindestens eine Datendatei wird wiederhergestellt. Während einer Dateiwiederherstellung sind die Dateigruppen, die die Dateien enthalten, automatisch offline. Wenn Sie versuchen, auf eine Offlinedateigruppe zuzugreifen, verursacht dies einen Fehler.  
  
-   Datenseite ( *Seitenwiederherstellung*)  
  
     Mit dem vollständigen Wiederherstellungsmodell oder dem massenprotokollierten Wiederherstellungsmodell können Sie einzelne Datenbanken wiederherstellen. Die Seitenwiederherstellung kann unabhängig von der Anzahl der Dateigruppen für jede Datenbank ausgeführt werden.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung und -Wiederherstellung funktioniert unter allen unterstützten Betriebssystemen, und zwar sowohl auf 64-Bit- als auch 32-Bit-Systemen. Informationen zu den unterstützten Betriebssystemen finden Sie unter [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). Informationen zur Unterstützung von Sicherungskopien früherer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen finden Sie im Kapitel [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)im Abschnitt „Kompatibilitätsunterstützung“.  
  
 **In diesem Thema:**  
  
-   [Übersicht über Wiederherstellungs Szenarien](#RestoreScenariosOv)  
  
-   [Wiederherstellungs Modelle und unterstützte Wiederherstellungs Vorgänge](#RMsAndSupportedRestoreOps)  
  
-   [Einschränkungen bei der Wiederherstellung mit dem einfachen Wiederherstellungs Modell](#RMsimpleScenarios)  
  
-   [Wiederherstellen mit dem Massen protokollierten Wiederherstellungs Modell](#RMblogRestore)  
  
-   [Daten Bank Wiederherstellungs Ratgeber (SQL Server Management Studio)](#DRA)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="RestoreScenariosOv"></a>Übersicht über Wiederherstellungs Szenarien  
 Ein *Wiederherstellungsszenario* in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist ein Prozess, der die Datenbank aus Daten von mindestens einer Sicherungskopie wiederherstellt. Die unterstützten Wiederherstellungsszenarien sind vom Wiederherstellungsmodell der Datenbank und der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]abhängig.  
  
 In der folgenden Tabelle werden die für die verschiedenen Wiederherstellungsmodelle unterstützten Wiederherstellungsszenarien eingeführt.  
  
|Wiederherstellungsszenario|Mit dem einfachen Wiederherstellungsmodell|Mit dem vollständigen/massenprotokollierten Wiederherstellungsmodell|  
|----------------------|---------------------------------|----------------------------------------------|  
|Vollständige Datenbankwiederherstellung|Dies ist die grundlegende Wiederherstellungsstrategie. Eine vollständige Datenbankwiederherstellung besteht möglicherweise nur im Wiederherstellen einer vollständigen Datenbanksicherung. Alternativ kann eine vollständige Datenbankwiederherstellung das Wiederherstellen einer vollständigen Datenbanksicherung, gefolgt vom Wiederherstellen einer differenziellen Sicherung, umfassen.<br /><br /> Weitere Informationen finden Sie unter [Vollständige Datenbankwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](complete-database-restores-simple-recovery-model.md).|Dies ist die grundlegende Wiederherstellungsstrategie. Eine vollständige Datenbankwiederherstellung bedeutet die Wiederherstellung einer vollständigen Datenbanksicherung und, optional, einer differenziellen Sicherung (soweit vorhanden), gefolgt von der Wiederherstellung aller darauffolgenden Protokollsicherungen (in chronologischer Reihenfolge). Um die vollständige Datenbankwiederherstellung abzuschließen, wird die letzte Protokollsicherung wiederhergestellt (RESTORE WITH RECOVERY).<br /><br /> Weitere Informationen finden Sie unter [Vollständige Datenbankwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](complete-database-restores-full-recovery-model.md).|  
|Dateiwiederherstellung**\***|Stellen Sie mindestens eine beschädigte schreibgeschützte Datei wieder her, ohne die gesamte Datenbank wiederherzustellen. Die Dateiwiederherstellung ist nur verfügbar, wenn die Datenbank mindestens eine schreibgeschützte Dateigruppe aufweist.|Wiederherstellen einer oder mehrerer Dateien ohne Wiederherstellung der gesamten Datenbank. Die Dateiwiederherstellung kann ausgeführt werden, während die Datenbank offline ist oder, bei einigen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], während die Datenbank online bleibt. Während einer Dateiwiederherstellung sind die Dateigruppen, die die wiederherzustellenden Dateien enthalten, immer offline.|  
|Seitenwiederherstellung|Nicht verfügbar|Stellt mindestens eine beschädigte Seite wieder her. Die Seitenwiederherstellung kann ausgeführt werden, während die Datenbank offline ist oder, bei einigen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], während die Datenbank online bleibt. Während einer Seitenwiederherstellung sind die wiederherzustellenden Seiten immer offline.<br /><br /> Es muss eine fortlaufende Kette von Protokollsicherungen bis zur aktuellen Protokolldatei vorhanden sein, und alle Protokollsicherungen müssen angewendet werden, um die Seite auf den Stand der aktuellen Protokolldatei zu bringen.<br /><br /> Weitere Informationen finden Sie unter [Wiederherstellung von Seiten &#40;SQL Server&#41;](restore-pages-sql-server.md).|  
|Schrittweise Wiederherstellung**\***|Stellen Sie die Datenbank in Phasen auf Dateigruppenebene wieder her, beginnend mit der primären Dateigruppe und allen sekundären Dateigruppen mit Lese-/Schreibzugriff.|Stellen Sie die Datenbank phasenweise auf Dateigruppenebene wieder her, beginnend mit der primären Dateigruppe.|  
  
 **\*** Die Online Wiederherstellung wird nur in der Enterprise Edition unterstützt.  
  
 Unabhängig davon, wie die Daten hergestellt werden, stellt [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] sicher, dass die gesamte Datenbank vor dem Wiederherstellen logisch konsistent ist. Beispielsweise können Sie eine Datei erst wiederherstellen und online schalten, wenn sie durch ein Rollforward auf einen Stand gebracht wurde, in dem sie mit der Datenbank konsistent ist.  
  
### <a name="advantages-of-a-file-or-page-restore"></a>Vorteile von Datei- oder Seitenwiederherstellungen  
 Das Wiederherstellen von Dateien oder Seiten anstelle der vollständigen Datenbank bietet folgende Vorteile:  
  
-   Bei der Wiederherstellung geringerer Datenmengen wird weniger Zeit zum Kopieren und Wiederherstellen benötigt.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist es u. U. möglich, dass während des Datei- oder Seitenwiederherstellungsprozesses andere Daten der Datenbank online bleiben.  
  
##  <a name="RMsAndSupportedRestoreOps"></a>Wiederherstellungs Modelle und unterstützte Wiederherstellungs Vorgänge  
 Die für eine Datenbank verfügbaren Wiederherstellungsvorgänge hängen vom Wiederherstellungsmodell ab. In der folgenden Tabelle finden Sie eine Zusammenfassung, ob und in welchem Ausmaß die verschiedenen Wiederherstellungsmodelle ein bestimmtes Wiederherstellungsszenario unterstützen.  
  
|Wiederherstellungsvorgang|Vollständiges Wiederherstellungsmodell|Massenprotokolliertes Wiederherstellungsmodell|Einfaches Wiederherstellungsmodell|  
|-----------------------|-------------------------|---------------------------------|---------------------------|  
|Datenwiederherstellung|Vollständige Wiederherstellung (falls das Protokoll verfügbar ist).|Gefahr des Datenverlusts.|Alle Daten seit der letzten vollständigen Sicherung oder differenziellen Sicherung gehen verloren.|  
|Point-in-Time-Wiederherstellung|Jeder von den Protokollsicherungen abgedeckte Zeitpunkt.|Nicht zulässig, wenn die Protokollsicherung massenprotokollierte Änderungen enthält.|Wird nicht unterstützt.|  
|Dateiwiederherstellung**\***|Vollständige Unterstützung.|Zuweilen.**\*\***|Verfügbar nur für schreibgeschützte sekundäre Dateien.|  
|Seiten Wiederherstellung**\***|Vollständige Unterstützung.|Zuweilen.**\*\***|Keine.|  
|Schrittweise Wiederherstellung (Dateigruppen Ebene)**\***|Vollständige Unterstützung.|Zuweilen.**\*\***|Verfügbar nur für schreibgeschützte sekundäre Dateien.|  
  
 **\*** Nur in der Enterprise Edition von verfügbar.[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 **\*\*** Informationen zu den erforderlichen Bedingungen finden Sie weiter unten in diesem Thema [unter Wiederherstellen von Einschränkungen unter dem einfachen Wiederherstellungs Modell](#RMsimpleScenarios).  
  
> [!IMPORTANT]  
>  Unabhängig vom Wiederherstellungsmodell einer Datenbank kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung nicht mit einer Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wiederhergestellt werden, die älter als die Version ist, mit der die Sicherung erstellt wurde.  
  
##  <a name="RMsimpleScenarios"></a>Wiederherstellungs Szenarien mit dem einfachen Wiederherstellungs Modell  
 Bei Verwendung des einfachen Wiederherstellungsmodells unterliegen Wiederherstellungsvorgänge den folgenden Einschränkungen:  
  
-   Die Dateiwiederherstellung und die schrittweise Wiederherstellung stehen nur für schreibgeschützte sekundäre Dateigruppen zur Verfügung. Informationen zu diesen Wiederherstellungsszenarien finden Sie unter [Dateiwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](file-restores-simple-recovery-model.md) und [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).  
  
-   Die Seitenwiederherstellung ist nicht zulässig.  
  
-   Die Wiederherstellung bis zu einem bestimmten Zeitpunkt ist nicht zulässig.  
  
 Wenn die genannten Einschränkungen für Ihre Anforderungen nicht geeignet sind, sollten Sie die Verwendung des vollständigen Wiederherstellungsmodells in Betracht ziehen. Weitere Informationen finden Sie unter [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
> [!IMPORTANT]  
>  Unabhängig vom Wiederherstellungsmodell einer Datenbank kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung nicht mit einer Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wiederhergestellt werden, die älter als die Version ist, mit der die Sicherung erstellt wurde.  
  
##  <a name="RMblogRestore"></a>Wiederherstellen mit dem Massen protokollierten Wiederherstellungs Modell  
 In diesem Abschnitt werden Aspekte der Wiederherstellung behandelt, die sich nur auf das massenprotokollierte Wiederherstellungsmodell beziehen, das als Zusatz zum vollständigen Wiederherstellungsmodell gedacht ist.  
  
> [!NOTE]  
>  Eine Einführung in das massenprotokollierte Wiederherstellungsmodell finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).  
  
 Im Allgemeinen ähnelt das massenprotokollierte Wiederherstellungsmodell dem vollständigen Wiederherstellungsmodell, und die für das vollständige Wiederherstellungsmodell beschriebenen Informationen gelten zudem für beide Modelle. Die Zeitpunktwiederherstellung und die Onlinewiederherstellung werden jedoch durch das massenprotokollierte Wiederherstellungsmodell beeinflusst.  
  
### <a name="restrictions-for-point-in-time-recovery"></a>Einschränkungen für die Zeitpunktwiederherstellung  
 Wenn eine Protokollsicherung, die im massenprotokollierten Wiederherstellungsmodell vorgenommen wurde, massenprotokollierte Änderungen enthält, ist eine Zeitpunktwiederherstellung nicht zulässig. Wenn versucht wird, eine Wiederherstellung bis zu einem bestimmten Zeitpunkt für eine Protokollsicherung auszuführen, die Massenänderungen enthält, treten beim Wiederherstellungsvorgang Fehler auf.  
  
### <a name="restrictions-for-online-restore"></a>Einschränkungen für die Onlinewiederherstellung  
 Eine Onlinewiederherstellungssequenz funktioniert nur, wenn folgende Bedingungen erfüllt werden:  
  
-   Alle erforderlichen Protokollsicherungen müssen vorgenommen werden, bevor die Wiederherstellungssequenz gestartet wird.  
  
-   Massenänderungen müssen gesichert werden, bevor die Onlinewiederherstellungssequenz gestartet wird.  
  
-   Wenn in der Datenbank Massenänderungen vorhanden sind, müssen alle Dateien online oder[defunct](remove-defunct-filegroups-sql-server.md)sein. (Dies bedeutet, dass die Datei kein Bestandteil der Datenbank mehr ist.)  
  
 Wenn diese Bedingungen nicht erfüllt werden, treten bei der Onlinewiederherstellungssequenz Fehler auf.  
  
> [!NOTE]  
>  Es empfiehlt sich, in das vollständige Wiederherstellungsmodell zu wechseln, bevor eine Onlinewiederherstellung gestartet wird. Weitere Informationen finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md).  
  
 Informationen zum Ausführen einer Onlinewiederherstellung finden Sie unter [Onlinewiederherstellungen &#40;SQL Server&#41;](online-restore-sql-server.md).  
  
##  <a name="DRA"></a>Daten Bank Wiederherstellungs Ratgeber (SQL Server Management Studio)  
 Der Datenbankwiederherstellungsberater erleichtert das Erstellen von Wiederherstellungsplänen, durch die optimale folgerichtige Wiederherstellungssequenzen implementiert werden. Viele bekannte Probleme mit der Datenbankwiederherstellung und von Kunden angeforderte Erweiterungen wurden behoben. Mit dem Datenbankwiederherstellungsberater werden u. a. folgende wichtige Erweiterungen eingeführt:  
  
-   **Restore-Plan-Algorithmus:**  Der zum Erstellen von Wiederherstellungs Plänen verwendete Algorithmus wurde erheblich verbessert, insbesondere bei komplexen Wiederherstellungs Szenarien. Viele Grenzfälle, einschließlich Verzweigungszenarien in Zeitpunktwiederherstellungen, werden effizienter als in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]behandelt.  
  
-   **Zeit Punkt** Wiederherstellungen:  Der Daten Bank Wiederherstellungs Ratgeber vereinfacht das Wiederherstellen einer Datenbank zu einem bestimmten Zeitpunkt erheblich. Die Unterstützung für Zeitpunktwiederherstellungen wird durch eine visuelle Sicherungszeitachse deutlich verbessert. Diese visuelle Zeitachse macht es möglich, einen geeigneten Zeitpunkt als Zielwiederherstellungspunkt zum Wiederherstellen einer Datenbank zu ermitteln. Die Zeitachse erleichtert das Durchlaufen eines verzweigten Wiederherstellungspfads (ein Pfad, der Wiederherstellungsverzweigungen umfasst). Ein angegebener Zeitpunktwiederherstellungsplan schließt automatisch die Sicherungen ein, die für das Wiederherstellen zum Zielzeitpunkt (Datum und Uhrzeit) relevant sind. Informationen finden Sie unter [Wiederherstellen einer SQL Server-Datenbank zu einem Zeitpunkt &#40;vollständiges Wiederherstellungsmodell&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
 Weitere Informationen zum Datenbankwiederherstellungsberater finden Sie in den folgenden Blogs zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltbarkeit:  
  
-   [Wiederherstellungs Ratgeber: eine Einführung](https://blogs.msdn.com/b/managingsql/archive/2011/07/13/recovery-advisor-an-introduction.aspx)  
  
-   [Wiederherstellungs Ratgeber: Verwenden von SSMS zum Erstellen/Wiederherstellen von getrennten Sicherungen](https://blogs.msdn.com/b/managingsql/archive/2011/07/13/recovery-advisor-using-ssms-to-create-restore-split-backups.aspx)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
 Keine.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)  
  
  
