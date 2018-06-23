---
title: Upgrade einer Datenbank-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a263e00df1978f09a77a4eeebbf90f0059fb2590
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149705"
---
# <a name="upgrade-database-engine"></a>Aktualisieren der Datenbank-Engine
  Dieses Thema enthält die Informationen, die Sie zur Vorbereitung und zum Verständnis des Aktualisierungsvorgangs benötigen. Dazu gehören:  
  
-   Bekannte Probleme bei der Aktualisierung  
  
-   Tasks und Überlegungen im Vorfeld der Aktualisierung  
  
-   Links zu Themen mit Verfahren für das Upgrade von [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Links zu Themen mit Verfahren zum Migrieren von Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Überlegungen zu Failoverclustern.  
  
-   Tasks und Überlegungen im Anschluss an die Aktualisierung.  
  
## <a name="known-upgrade-issues"></a>Bekannte Probleme bei Aktualisierungen.  
 Lesen Sie vor der Aktualisierung von [!INCLUDE[ssDE](../../includes/ssde-md.md)] das Thema [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../sql-server-database-engine-backward-compatibility.md). Informationen zu Szenarien und bekannten Problemen beim Upgrade finden Sie unter [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md). Informationen zur Abwärtskompatibilität anderer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten finden Sie unter [Abwärtskompatibilität](../../getting-started/backward-compatibility.md).  
  
> [!IMPORTANT]  
>  Bevor Sie eine Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf eine andere Edition aktualisieren, sollten Sie überprüfen, ob die derzeit verwendete Funktionalität in der Edition, die Ziel des Upgrades ist, unterstützt wird.  
  
> [!NOTE]  
>  Wenn Sie von einer früheren Version der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise-Edition auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren, wählen Sie zwischen "Enterprise Edition: Core-basierte Lizenzierung" und "Enterprise Edition" aus. Diese Enterprise Editionen unterscheiden sich nur im Hinblick auf den Lizenzierungsmodus. Weitere Informationen finden Sie unter [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
## <a name="pre-upgrade-checklist"></a>Prüfliste vor der Aktualisierung  
 Das Setupprogramm von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Upgrade von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können auch Datenbanken von früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] migrieren. Die Migration kann von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zu einer anderen auf demselben Computer oder zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz auf einem anderen Computer erfolgen. Migrationsoptionen umfassen die Verwendung des Assistenten zum Kopieren von Datenbanken, Sichern und wiederherstellen, mit der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Import / Export-Assistenten und Massenexport/Methoden importieren.  
  
 Lesen Sie vor dem Upgrade von [!INCLUDE[ssDE](../../includes/ssde-md.md)]die folgenden Themen:  
  
-   Informieren Sie sich unter [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Informieren Sie sich unter [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md).  
  
-   Informieren Sie sich unter [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Informieren Sie sich unter [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md).  
  
-   Informieren Sie sich unter [Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   Informieren Sie sich unter [Vorbereiten von Upgrades mit dem Distributed Replay Utility](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md).  
  
-   Informieren Sie sich unter [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../sql-server-database-engine-backward-compatibility.md).  
  
-   Informieren Sie sich unter [Migrieren von Abfrageplänen](change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
 Überprüfen Sie die folgenden Probleme, und nehmen Sie nach Bedarf Änderungen vor dem Upgrade auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vor:  
  
-   Wenn Sie Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren, wo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent in MSX/TSX-Beziehungen eingetragen wird, aktualisieren Sie Zielserver vor den Masterservern. Wenn Sie Masterserver vor den Zielservern aktualisieren, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent keine Verbindung mit den Masterinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen.  
  
-   Wenn Sie von einer 64-Bit-Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf eine 64-Bit-Edition von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisieren, müssen Sie vor dem Upgrade von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] aktualisieren.  
  
-   Sichern Sie alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankdateien der zu aktualisierenden Instanz, damit diese bei Bedarf wiederhergestellt werden können.  
  
-   Führen Sie die entsprechenden Datenbank-Konsolenbefehle (Database Console Commands, DBCC) für die zu aktualisierenden Datenbanken aus, um deren Konsistenz sicherzustellen.  
  
-   Schätzen Sie ab, wie viel Speicherplatz für das Upgrade von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten sowie der Benutzerdatenbanken erforderlich ist. Informationen zum erforderlichen Speicherplatz für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Stellen Sie sicher, dass für vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatenbanken – master, model, msdb und tempdb – die automatische Vergrößerung konfiguriert ist, und stellen Sie sicher, dass ausreichend Festplattenspeicherplatz verfügbar ist.  
  
-   Stellen Sie sicher, dass alle Datenbankserver über Anmeldeinformationen in der master-Datenbank verfügen. Dies ist wichtig für das Wiederherstellen einer Datenbank, da sich die Systemanmeldeinformationen in der master-Datenbank befinden.  
  
-   Deaktivieren Sie alle gespeicherten Startprozeduren, da im Rahmen des Upgradeprozesses auch Dienste auf der zu aktualisierenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz beendet und gestartet werden. Der Aktualisierungsprozess kann durch beim Start verarbeitete gespeicherte Prozeduren blockiert werden.  
  
-   Stellen Sie sicher, dass die Replikation aktuell ist, und beenden Sie die Replikation.  
  
-   Beenden Sie alle Anwendungen sowie alle Dienste mit Abhängigkeiten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Verbindungen von lokalen Anwendungen mit der zu aktualisierenden Instanz bestehen, kann das Upgrade einen Fehler erzeugen.  
  
-   Wenn Sie Datenbankspiegelung verwenden, sollten Sie [Minimieren der Ausfallzeit von gespiegelten Datenbanken beim Aktualisieren von Serverinstanzen](../database-mirroring/upgrading-mirrored-instances.md) lesen.  
  
## <a name="upgrading-the-database-engine"></a>Aktualisieren der Datenbank-Engine  
 Eine Installation von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher kann durch ein Versionsupgrade überschrieben werden. Wenn bei der Ausführung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkannt wird, werden alle früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Programmdateien aktualisiert, und die in der früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz gespeicherten Daten werden beibehalten. Darüber hinaus bleiben auf dem Computer auch frühere Versionen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation intakt.  
  
> [!WARNING]  
>  Beim Ausführen des Setup-Programms von SQL Server 2014 wird die SQL Server-Instanz im Rahmen der vor dem Upgrade erfolgenden Überprüfungen beendet und neu gestartet.  
  
> [!CAUTION]  
>  Wenn Sie auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren, wird die frühere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz überschrieben und ist auf dem Computer folglich nicht mehr vorhanden. Sichern Sie vor dem Upgrade die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken und alle anderen der früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zugeordneten Objekte.  
  
 Sie können [!INCLUDE[ssDE](../../includes/ssde-md.md)] aktualisieren, indem Sie den Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden.  
  
### <a name="database-compatibility-level-after-upgrade"></a>Datenbank-Kompatibilitätsgrad nach dem Upgrade  
 Der Kompatibilitätsgrad der der `tempdb`, `model`, `msdb` und **Ressource** Datenbanken nach dem Upgrade auf jeweils 120 festgelegt. Die `master`-Systemdatenbank behält den Kompatibilitätsgrad von vor dem Upgrade bei.  
  
 War der Kompatibilitätsgrad einer Benutzerdatenbank vor dem Upgrade 100 oder höher, wird er nach dem Upgrade beibehalten. War der Kompatibilitätsgrad der aktualisierten Datenbank vor dem Upgrade 90, wird er auf 100 gesetzt, was dem niedrigsten unterstützten Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]entspricht.  
  
> [!NOTE]  
>  Neue Benutzerdatenbanken erben den Kompatibilitätsgrad der `model` Datenbank.  
  
## <a name="migrating-databases"></a>Migrieren von Datenbanken  
 Mithilfe der Sicherungs- und Wiederherstellungs- oder der Trennungs- und Anfügungsfunktionalitäten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie Benutzerdatenbanken in eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verschieben. Weitere Informationen finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) und unter [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
> [!IMPORTANT]  
>  Eine Datenbank mit identischem Namen auf dem Quell- und dem Zielserver kann nicht verschoben oder kopiert werden. In diesem Fall wird erkannt, dass die Datenbank "bereits vorhanden" ist.  
  
 Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="after-upgrading-the-database-engine"></a>Nach Aktualisierung der Datenbank-Engine  
 Führen Sie nach dem Aktualisieren von [!INCLUDE[ssDE](../../includes/ssde-md.md)]die folgenden Aufgaben aus:  
  
-   Registrieren Sie die Server neu. Weitere Informationen zum Registrieren von Servern finden Sie unter [Registrieren von Servern](../../ssms/register-servers/register-servers.md).  
  
-   Füllen Sie die Volltextkataloge wieder auf, um eine konsistente Semantik in Abfrageergebnissen zu gewährleisten.  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert neue Wörtertrennungen, die von der Volltextsuche und semantischen Suche verwendet werden. Die Wörtertrennungen werden sowohl bei der Indizierung als auch bei Abfragen verwendet. Wenn Sie die Volltextkataloge nicht neu erstellen, sind die Suchergebnisse möglicherweise inkonsistent. Wenn Sie eine Volltextabfrage senden, die nach einem Ausdruck sucht, der von der Wörtertrennung in einer früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version und der aktuellen Wörtertrennung unterschiedlich getrennt wird, können Dokumente oder Zeilen, in denen der Ausdruck enthalten ist, möglicherweise nicht abgerufen werden. Das liegt daran, dass die indizierten Ausdrücke anhand einer anderen Logik getrennt wurden als der von der Abfrage verwendeten Logik. Die Lösung besteht darin, die Volltextkataloge mit den neuen Wörtertrennungen aufzufüllen (neu zu erstellen), damit das Verhalten bei der Indizierung und bei Abfragen gleich ist.  
  
     Weitere Informationen finden Sie unter [sp_fulltext_catalog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql).  
  
-   Konfigurieren Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation. Zum Reduzieren der Angriffsfläche eines Systems werden zentrale Dienste und Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selektiv installiert und aktiviert.  
  
-   Überprüfen oder entfernen Sie USE PLAN-Hinweise, die von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] generiert werden und auf Abfragen auf partitionierte Tabellen und Indizes angewendet werden.  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ändert die Abfragen auf partitionierte Tabellen und Indizes verarbeitet werden. Abfragen von partitionierten Objekte, die den USE PLAN-Hinweis für einen von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] generierten Plan verwenden, enthalten u. U. einen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ungültigen Plan. Wir empfehlen die folgenden Prozeduren, nachdem Sie auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisiert haben.  
  
     **Wenn USE PLAN-Hinweis direkt in einer Abfrage angegeben wird:**  
  
    1.  Entfernen Sie den USE PLAN-Hinweis aus der Abfrage.  
  
    2.  Testen Sie die Abfrage.  
  
    3.  Wenn der Optimierer keinen geeigneten Plan auswählt, optimieren Sie die Abfrage, und geben Sie ggf. den USE PLAN-Hinweis mit dem gewünschten Abfrageplan ein.  
  
     **Wenn der USE PLAN-Hinweis in einer Planhinweisliste angegeben wird:**  
  
    1.  Verwenden Sie die sys.fn_validate_plan_guide-Funktion, um die Gültigkeit der Planhinweisliste zu überprüfen. Alternativ können Sie auch mit dem Plan Guide Unsuccessful-Ereignis in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]nach ungültigen Planhinweislisten suchen.  
  
    2.  Wenn die Planhinweisliste nicht gültig ist, verwerfen Sie sie. Wenn der Optimierer keinen geeigneten Plan auswählt, optimieren Sie die Abfrage, und geben Sie ggf. den USE PLAN-Hinweis mit dem gewünschten Abfrageplan ein.  
  
     Ein ungültiger Plan führt nicht zu einem Abfragefehler, wenn der USE PLAN-Hinweis in einer Planhinweisliste angegeben ist. Stattdessen wird die Abfrage kompiliert, ohne den USE PLAN-Hinweis zu verwenden.  
  
 Datenbanken, die vor der Aktualisierung als volltextfähig oder nicht volltextfähig gekennzeichnet wurden, behalten ihren Status auch nach der Aktualisierung bei. Die Volltextkataloge werden bei volltextfähigen Datenbanken nach der Aktualisierung neu erstellt und automatisch aufgefüllt. Dieser Vorgang ist sehr zeitaufwändig und ressourcenintensiv. Um die Volltextindizierung vorübergehend anzuhalten, führen Sie folgende Anweisung aus:  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 1;  
```  
  
 Um die Auffüllung des Volltextindexes fortzusetzen, führen Sie folgende Anweisung aus:  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 0;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md)   
 [Verwenden Sie mehrerer Versionen und Instanzen von SQLServer](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [Abwärtskompatibilität](../../getting-started/backward-compatibility.md)   
 [Aktualisieren von replizierten Datenbanken](upgrade-replicated-databases.md)  
  
  
