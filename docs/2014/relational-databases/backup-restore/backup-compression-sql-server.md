---
title: Sicherungskomprimierung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: af3e8d9184b12a726361643c563402242c6b04cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62876784"
---
# <a name="backup-compression-sql-server"></a>Sicherungskomprimierung (SQL Server)
  In diesem Thema wird die Komprimierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen beschrieben, einschließlich Einschränkungen und Leistungseinbußen bei der Sicherungskomprimierung, Konfiguration der Sicherungskomprimierung sowie Komprimierungsverhältnis.  
  
> [!NOTE]  
>  Informationen zu den Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , die die Sicherungs Komprimierung unterstützen, finden Sie unter [von den Editionen von SQL Server 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Jede Edition von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höhere Versionen können eine komprimierte Sicherung wiederherstellen.  
  
  
##  <a name="Benefits"></a> Vorteile  
  
-   Da eine komprimierte Sicherung kleiner als eine unkomprimierte Sicherung derselben Daten ist, wird für das Komprimieren einer Sicherung normalerweise weniger Geräte-E/A benötigt, und daher steigt die Sicherungsgeschwindigkeit in der Regel erheblich.  
  
     Weitere Informationen finden Sie unter [Auswirkungen der Sicherungskomprimierung auf die Leistung](#PerfImpact)weiter unten in diesem Thema.  
  
  
##  <a name="Restrictions"></a> Einschränkungen  
 Für komprimierte Sicherungen gelten die folgenden Einschränkungen:  
  
-   Komprimierte und nicht komprimierte Sicherungen können nicht nebeneinander in einem Mediensatz bestehen.  
  
-   Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können komprimierte Sicherungen nicht lesen.  
  
-   Mit "NTbackup" erstellte Sicherungen können nicht auf demselben Band gespeichert werden wie komprimierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen.  
  
  
##  <a name="PerfImpact"></a> Auswirkungen der Sicherungskomprimierung auf die Leistung  
 Standardmäßig steigt die CPU-Nutzung durch die Komprimierung erheblich, und die bei der Komprimierung zusätzlich verbrauchten CPU-Ressourcen können sich negativ auf gleichzeitige Vorgänge auswirken. Daher ist es u.U. sinnvoll, in einer Sitzung, bei der die CPU-Nutzung durch[Resource Governor](../resource-governor/resource-governor.md)eingeschränkt ist, komprimierte Sicherungen mit niedriger Priorität zu erstellen. Weitere Informationen finden Sie unter [Einschränken der CPU-Nutzung durch die Sicherungskomprimierung mithilfe der Ressourcenkontrolle &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).  
  
 Wenn Sie genau wissen möchten, welche Leistung die Sicherungs-E/A erbringt, können Sie die Sicherungs-E/A zu und von den Geräten beurteilen, indem Sie die folgenden Arten von Leistungsindikatoren analysieren:  
  
-   Windows-E/A-Leistungsindikatoren, wie die Indikatoren für physische Datenträger  
  
-   Der Leistungsindikator **Mediumsdurchsatz Bytes/Sekunde** des Objekts [SQLServer:Sicherungsmedium](../performance-monitor/sql-server-backup-device-object.md)  
  
-   Der Leistungsindikator **Sicherungs-/Wiederherstellungsdurchsatz/Sekunde** des Objekts [SQLServer:Datenbanken](../performance-monitor/sql-server-databases-object.md)  
  
 Informationen zu den Windows-Indikatoren finden Sie in der Windows-Hilfe. Informationen zur Arbeit mit SQL Server-Indikatoren finden Sie unter [Verwenden von SQL Server-Objekten](../performance-monitor/use-sql-server-objects.md).  
  
  
##  <a name="CompressionRatio"></a> Berechnen des Komprimierungsverhältnisses einer komprimierten Sicherung  
 Zum Berechnen des Komprimierungsverhältnisses einer Sicherung verwenden Sie die Werte für die Sicherung in den Spalten **backup_size** und **compressed_backup_size** der Verlaufstabelle [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) wie folgt:  
  
 **backup_size**:**compressed_backup_size**  
  
 So gibt ein Komprimierungsverhältnis von 3:1 beispielsweise an, dass Sie etwa 66 Prozent an Speicherplatz sparen. Für eine Abfrage in diesen Spalten können Sie die folgende Transact-SQL-Anweisung verwenden:  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 Das Komprimierungsverhältnis einer komprimierten Sicherung ist abhängig von den komprimierten Daten. Das erzielte Komprimierungsverhältnis kann durch eine Reihe von Faktoren beeinflusst werden. Zu den Hauptfaktoren gehören:  
  
-   Die Art der Daten.  
  
     Zeichendaten lassen sich stärker komprimieren als andere Arten von Daten.  
  
-   Die Einheitlichkeit der Daten unter den Zeilen einer Seite.  
  
     In der Regel enthält eine Seite mehrere Zeilen, in denen ein Feld den gleichen Wert aufweist. Dieser Wert kann möglicherweise sehr stark komprimiert werden. Dagegen ist bei Datenbanken mit Zufallsdaten oder nur einer großen Zeile pro Seite die komprimierte Sicherung beinahe so groß wie eine nicht komprimierte Sicherung.  
  
-   Verschlüsselungsstatus der Daten.  
  
     Verschlüsselte Daten lassen sich deutlich weniger komprimieren als entsprechende unverschlüsselte Daten. Wird die transparente Datenverschlüsselung zum Verschlüsseln einer gesamten Datenbank verwendet, ändert sich ihre Größe bei einer komprimierten Sicherung unter Umständen kaum oder gar nicht.  
  
-   Komprimierungsstatus der Datenbank.  
  
     Falls die Datenbank bereits komprimiert ist, ändert sich ihre Größe bei einer komprimierten Sicherung unter Umständen kaum oder gar nicht.  
  
  
##  <a name="Allocation"></a> Speicherplatzzuordnung für die Sicherungsdatei  
 Bei komprimierten Sicherungen ist die Größe der finalen Sicherungsdatei davon abhängig, wie stark die Daten komprimiert werden können, und dies ist erst bekannt, wenn der Sicherungsvorgang abgeschlossen ist.  Wenn eine Datenbank daher mithilfe einer Komprimierung gesichert wird, verwendet die Datenbank-Engine standardmäßig einen Vorabzuordnungsalgorithmus für die Sicherungsdatei. Dieser Algorithmus ordnet der Sicherungsdatei vorab einen vordefinierten Prozentsatz der Größe der Datenbank zu. Wenn während des Sicherungsvorgangs mehr Platz benötigt wird, lässt die Datenbank-Engine die Datei wachsen. Wenn die finale Größe kleiner als der reservierte Platz ist, verkleinert die Datenbank-Engine die Datei am Ende des Sicherungsvorgangs auf die tatsächliche finale Größe der Sicherung.  
  
 Verwenden Sie das Ablaufverfolgungsflag 3042, damit die Sicherungsdatei nur so viel größer werden kann, wie erforderlich, um die finale Größe zu erreichen. Durch das Ablaufverfolgungsflag 3042 wird bewirkt, dass der Sicherungsvorgang den standardmäßigen Vorabzuordnungsalgorithmus für die Sicherungskomprimierung umgeht. Dieses Ablaufverfolgungsflag ist nützlich, wenn Sie Speicherplatz einsparen müssen, indem Sie nur die tatsächliche für die komprimierte Sicherung benötigte Größe zuordnen. Dieses Ablaufverfolgungsflag kann jedoch eine leichte Leistungseinbuße (eine mögliche Verlängerung des Sicherungsvorgangs) verursachen.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Konfigurieren von Sicherungskomprimierung &#40;SQL Server&#41;](backup-compression-sql-server.md)  
  
-   [Anzeigen oder Konfigurieren der Serverkonfigurationsoption Standardeinstellung für die Sicherungskomprimierung](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [Einschränken der CPU-Nutzung durch die Sicherungskomprimierung mithilfe der Ressourcenkontrolle &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [DBCC TRACEOFF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
