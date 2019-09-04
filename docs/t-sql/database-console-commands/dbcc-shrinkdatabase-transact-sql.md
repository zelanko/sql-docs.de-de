---
title: DBCC SHRINKDATABASE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_SHRINKDATABASE_TSQL
- DBCC SHRINKDATABASE
- SHRINKDATABASE_TSQL
- SHRINKDATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- shrinking files
- shrinking databases
- DBCC SHRINKDATABASE statement
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
ms.assetid: fc976afd-1edb-4341-bf41-c4a42a69772b
author: pmasl
ms.author: umajay
monikerRange: = azuresqldb-current ||>= sql-server-2016 ||>= sql-server-linux-2017||=azure-sqldw-latest||= sqlallproducts-allversions
ms.openlocfilehash: 1bda4ebd946bfd8adf31190c36125075d50dc28d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073163"
---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Reduziert die Größe der Daten- und Protokolldateien in der angegebenen Datenbank.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC SHRINKDATABASE   
( database_name | database_id | 0   
     [ , target_percent ]   
     [ , { NOTRUNCATE | TRUNCATEONLY } ]   
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
_database\_name_ | _database\_id_ | 0  
Dies ist der Name oder die ID der Datenbank, die verkleinert werden soll. Mit „0“ (null) wird angegeben, dass die aktuelle Datenbank verwendet wird.  
  
_target\_percent_  
Der gewünschte Prozentsatz an freiem Speicherplatz, der in der Datenbankdatei übrig bleiben soll, nachdem die Datenbank verkleinert wurde.  
  
NOTRUNCATE  
Hiermit werden zugewiesene Seiten vom Dateiende zu nicht zugewiesenen Seiten am Dateianfang verschoben. Mit dieser Aktion werden die Daten in der Datei komprimiert. Das Argument _target\_percent_ ist optional. Azure SQL Data Warehouse unterstützt diese Option nicht. 
  
Der freie Speicherplatz am Dateiende wird nicht an das Betriebssystem zurückgegeben, und die physische Größe der Datei bleibt unverändert. Daher scheint die Datenbank, bei Angabe von NOTRUNCATE nicht kleiner zu werden.  
  
NOTRUNCATE gilt nur für Datendateien. NOTRUNCATE wirkt sich nicht auf die Protokolldatei aus.  
  
TRUNCATEONLY  
Hiermit wird der gesamte freie Speicherplatz am Ende der Datei für das Betriebssystem freigegeben. Seiten in der Datei werden nicht verschoben. Die Datendatei wird nur auf die zuletzt zugewiesene Erweiterung verkleinert. Das Argument _target\_percent_ wird ignoriert, wenn es mit TRUNCATEONLY angegeben wird. Azure SQL Data Warehouse unterstützt diese Option nicht.
  
TRUNCATEONLY wirkt sich auf die Protokolldatei aus. Um nur die Datendatei abzuschneiden, verwenden Sie DBCC SHRINKFILE.  
  
WITH NO_INFOMSGS  
Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.  
  
## <a name="result-sets"></a>Resultsets  
In der folgenden Tabelle werden die Spalten des Resultsets beschrieben:
  
|Spaltenname|und Beschreibung|  
|-----------------|-----------------|  
|**DbId**|Die Datenbank-ID der Datei, die das [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu verkleinern versuchte.|  
|**FileId**|Datei-ID der Datei, die das [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu verkleinern versuchte.|  
|**CurrentSize**|Die Anzahl von 8-KB-Seiten, die die Datei derzeit belegt.|  
|**MinimumSize**|Die Anzahl von 8-KB-Seiten, die die Datei minimal belegen könnte. Dieser Wert entspricht der Mindestgröße bzw. der ursprünglich erzeugten Dateigröße.|  
|**UsedPages**|Die Anzahl von 8-KB-Seiten, die derzeit von der Datei verwendet werden.|  
|**EstimatedPages**|Die Anzahl an 8-KB-Seiten, auf die die Datei wahrscheinlich vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] verkleinert werden kann.|  
  
>[!NOTE]
> Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] zeigt keine Zeilen für Dateien an, die nicht verkleinert wurden.  
  
## <a name="remarks"></a>Bemerkungen  

>[!NOTE]
> Aktuell wird DBCC SHRINKDATABASE von Azure SQL Data Warehouse nicht unterstützt. Das Ausführen dieses Befehls wird nicht empfohlen, da der Vorgang sehr E/A-intensiv ist und Ihr Datawarehouse offline schalten kann. Darüber hinaus ändern sich die Kosten Ihrer Datawarehouse-Momentaufnahmen nach dem Ausführen dieses Befehls. 

Zum Verkleinern aller Daten- und Protokolldateien einer bestimmten Datenbank führen Sie den DBCC SHRINKDATABASE-Befehl aus. Führen Sie zum Verkleinern einer einzelnen Daten- oder Protokolldatei einer bestimmten Datenbank den Befehl [DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) aus.
  
Führen Sie [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) zum Anzeigen des aktuellen freien (nicht zugeordneten) Speicherplatzes in der Datenbank aus.
  
DBCC SHRINKDATABASE-Vorgänge können an jeder Stelle des Vorgangs beendet werden, wobei der bereits abgeschlossene Anteil erhalten bleibt.
  
Die Datenbank kann nicht kleiner als die konfigurierte Mindestgröße der Datenbank sein. Die Mindestgröße legen Sie bei der ursprünglichen Erstellung der Datenbank fest. Die Mindestgröße kann alternativ die letzte explizit festgelegte Größe sein, die mithilfe eines Vorgangs für die Dateigrößenänderung festgelegt wurde. Vorgänge wie DBCC SHRINKFILE oder ALTER DATABASE sind Beispiele für Vorgänge für Dateigrößenänderungen. 

Angenommen eine Datenbank wurde ursprünglich mit einer Größe von 10 MB erstellt. Dann erreicht diese Datenbank eine Größe von 100 MB. Die Mindestgröße, auf die die Datenbank verkleinert werden kann, beträgt 10 MB. Dies gilt auch, wenn alle Daten in der Datenbank gelöscht werden.
  
Legen Sie beim Ausführen von DBCC SHRINKDATABASE entweder die Option NOTRUNCATE oder TRUNCATEONLY fest. Wenn Sie dies nicht tun, gleicht das Ergebnis der Ausführung des Vorgangs DBCC SHRINKDATABASE mit NOTRUNCATE mit einer anschließenden Ausführung von DBCC SHRINKDATABASE mit TRUNCATEONLY.
  
Die verkleinerte Datenbank muss sich nicht im Einzelbenutzermodus befinden. Andere Benutzer können an der Datenbank arbeiten, wenn sie verkleinert wird. Dies gilt auch für Systemdatenbanken.
  
Sie können eine Datenbank nicht verkleinern, während sie gesichert wird. Sie können eine Datenbank hingegen auch nicht sichern, während ein Verkleinerungsvorgang für die Datenbank durchgeführt wird.
  
## <a name="how-dbcc-shrinkdatabase-works"></a>Funktionsweise von DBCC SHRINKDATABASE  
DBCC SHRINKDATABASE verkleinert Datendateien pro Datei, Protokolldateien jedoch so, als lägen alle Protokolldateien in einem zusammenhängenden Protokollpool vor. Dateien werden immer am Ende verkleinert.
  
Angenommen Sie verfügen über mehrere Protokolldateien, eine Datendatei und eine Datenbank namens **mydb**. Die Datendatei und die Protokolldateien sind jeweils 10 MB groß, die Datendatei enthält 6 MB an Daten. Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] berechnet für jede Datei eine Zielgröße. Auf diesen Wert soll die Datei verkleinert werden. Wenn DBCC SHRINKDATABASE mit _target\_percent_ angegeben wird, dann berechnet die [!INCLUDE[ssDE](../../includes/ssde-md.md)] einen prozentualen Anteil von _target\_percent_ als Zielgröße des freien Speicherplatzes der Datei nach der Verkleinerung. 

Wenn Sie für die Verkleinerung von **mydb** beispielsweise den Wert 25 für _target\_percent_ angeben, dann berechnet die [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Zielgröße für die Datendatei mit 8 MB (6 MB Daten plus 2 MB freier Speicherplatz). Daher verschiebt die [!INCLUDE[ssDE](../../includes/ssde-md.md)] alle Daten aus den letzten 2 MB der Datendatei in beliebigen freien Speicherplatz in den ersten 8 MB der Datendatei und verkleinert dann die Datei.
  
Angenommen, die Datendatei von **mydb** enthält 7 MB Daten. Durch die Angabe eines _target\_percent_-Werts von 30 kann diese Datendatei auf einen freien Prozentsatz von 30 % verkleinert werden. Durch die Angabe eines _target\_percent_-Werts von 40 wird die Datendatei jedoch nicht verkleinert, da die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Dateien nicht auf eine Größe verkleinert, die unter dem von den Daten belegten Speicherplatz liegt. 

Sie können sich das Problem auch wie folgt vorstellen: 40 % erwünschter freier Speicherplatz plus eine zu 70 % volle Datendatei (7 MB von 10 MB) ergeben mehr als 100 %. Bei jedem _target\_size_-Wert, der über 30 liegt, wird die Datendatei nicht verkleinert. Sie wird nicht verkleinert, weil der gewünschte freie Prozentsatz plus dem aktuell von der Datendatei belegten Prozentsatz einen Wert über 100 % ergibt.
  
Für Protokolldateien verwendet die [!INCLUDE[ssDE](../../includes/ssde-md.md)] _target\_percent_, um die Zielgröße für das gesamte Protokoll zu berechnen. Deshalb entspricht _target\_percent_ nach dem Verkleinerungsvorgang dem freien Speicherplatz im Protokoll. Die Zielgröße für das gesamte Protokoll wird dann in eine Zielgröße für jede Protokolldatei umgewandelt.
  
DBCC SHRINKDATABASE versucht, jede physische Protokolldatei sofort auf ihre Zielgröße zu verkleinern. Angenommen, abgesehen von der Dateigröße der Protokolldatei bleiben keine Bestandteile des logischen Protokolls in den virtuellen Protokollen zurück. Die Datei wird dann erfolgreich gekürzt, und der Vorgang DBCC SHRINKDATABASE wird ohne Meldungen abgeschlossen. Wenn sich dagegen ein Teil des logischen Protokolls in den virtuellen Protokollen befindet, die außerhalb der Zielgröße liegen, gibt die [!INCLUDE[ssDE](../../includes/ssde-md.md)] so viel Speicherplatz wie möglich frei und gibt dann eine Informationsmeldung aus. Die Meldung beschreibt, welche Aktionen erforderlich sind, um das logische Protokoll aus den virtuellen Protokollen am Ende der Datei zu verschieben. Nachdem diese Aktionen ausgeführt wurden, kann der verbleibende Speicherplatz mit DBCC SHRINKDATABASE freigegeben werden.
  
Protokolldateien können nur auf den Grenzwert für virtuelle Protokolldateien verkleinert werden. Aus diesem Grund können Protokolldateien nicht auf eine kleinere Größe als virtuelle Protokolldateien verkleinert werden. Dies ist möglicherweise auch nicht möglich, wenn sie nicht verwendet werden. Die Größe der virtuellen Protokolldatei wird dynamisch vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgewählt, wenn Protokolldateien erstellt oder erweitert werden.
  
## <a name="best-practices"></a>Bewährte Methoden  
Berücksichtigen Sie die folgenden Informationen, wenn Sie eine Datenbank verkleinern möchten:
-   Verkleinerungsvorgänge sind nach anderen Vorgängen am effektivsten. Mit diesen Vorgängen (z.B. TRUNCATE TABLE oder DROP TABLE) wird ungenutzter Speicherplatz geschaffen.  
-   Die meisten Datenbanken erfordern verfügbaren freien Speicherplatz für die normalen alltäglichen Vorgänge. Möglicherweise wird Ihnen auffallen, dass die Größe der Datenbank wieder steigt, wenn Sie sie wiederholt verkleinern. Dieses Wachstum gibt an, dass der verkleinerte Speicherplatz für normale Vorgänge erforderlich ist. In diesem Fall ist das Verkleinern der Datenbank vergeblich.  
-   Bei einem Verkleinerungsvorgang bleibt der Fragmentierungszustand der Indizes in der Datenbank nicht erhalten. Im Allgemeinen wird die Fragmentierung zu einem gewissen Grad verstärkt. Dies ist ein weiterer Grund, die Datenbank nicht wiederholt zu verkleinern.  
-   Legen Sie die Datenbankoption AUTO_SHRINK nicht auf ON fest, es sei denn, besondere Anforderungen erfordern dies.  
  
## <a name="troubleshooting"></a>Problembehandlung  
Es kann vorkommen, dass Verkleinerungsvorgänge durch eine Transaktion blockiert werden, die auf einer auf [Zeilenversionsverwaltung basierenden Isolationsstufe](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md) ausgeführt wird. Beispiel: Ein umfangreicher Löschvorgang wird auf einer auf Zeilenversionsverwaltung basierenden Isolationsstufe ausgeführt, und ein DBCC SHRINKDATABASE-Vorgang wird ausgeführt. In diesem Fall wartet der Verkleinerungsvorgang auf den Abschluss des Löschvorgangs, bevor die Dateien verkleinert werden. Während der Verkleinerungsvorgang wartet, wird von den DBCC SHRINKFILE- und DBCC SHRINKDATABASE-Vorgängen eine Informationsmeldung (5202 für SHRINKDATABASE und 5203 für SHRINKFILE) ausgegeben. Diese Meldung zeigt in der ersten Stunde alle fünf Minuten und dann jede Stunde das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll an. Das Fehlerprotokoll kann beispielsweise eine Fehlermeldung wie die folgende enthalten:  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Dieser Fehler bedeutet, dass Momentaufnahmetransaktionen, mit Zeitstempeln über 109 den Verkleinerungsvorgang blockieren. Diese Transaktion ist die letzte, die der Verkleinerungsvorgang abschließt. Außerdem wird angezeigt, dass die Spalte **transaction_sequence_num** oder **first_snapshot_sequence_num** in der dynamischen Verwaltungssicht [sys.dm_tran_active_snapshot_database_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) einen Wert von 15 enthält. Die Spalte **transaction_sequence_num** oder **first_snapshot_sequence_num** in der Sicht enthalten möglicherweise eine Zahl, die kleiner als die der letzten Transaktion ist, die vom Verkleinerungsvorgang (109) abgeschlossen wurde. Wenn dies der Fall ist, wartet der Verkleinerungsvorgang auf den Abschluss dieser Transaktionen.
  
Führen Sie eine der folgenden Aufgaben aus, um das Problem zu beheben:
-   Beenden Sie die Transaktion, die den Verkleinerungsvorgang blockiert.  
-   Beenden Sie den Verkleinerungsvorgang. Die bereits abgeschlossene Arbeit bleibt erhalten.  
-   Führen Sie keine besonderen Aktionen aus, und lassen Sie zu, dass mit dem Verkleinerungsvorgang gewartet wird, bis die blockierende Transaktion abgeschlossen ist.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. Verkleinern einer Datenbank und Angeben des freien Speicherplatzes in Prozent  
Im folgenden Beispiel wird die Größe der Daten- und Protokolldateien in der `UserDB`-Benutzerdatenbank so verringert, dass die Datenbank 10 % freien Speicherplatz enthält.  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>B. Abschneiden einer Datenbank  
Im folgenden Beispiel werden die Daten- und Protokolldateien in der `AdventureWorks`-Beispieldatenbank auf die letzte zugeordnete Erweiterung verkleinert.  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>Siehe auch  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[Verkleinern einer Datenbank](../../relational-databases/databases/shrink-a-database.md)
  
  
