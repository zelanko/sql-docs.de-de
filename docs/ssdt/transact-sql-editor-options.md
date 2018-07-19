---
title: Optionen des Transact-SQL-Editors | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_RESULTS.RESULTS_TO_GRID
- sql.data.tools.SqlExecutionAdvancedSettingsOption
- sql.data.tools.SqlExecutionAnsiSettingsDlg
- sql.data.tools.SqlResultToTextSettingsDlg
- sql.data.tools.SqlExecutionGeneralSettingsDlg
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_RESULTS.GENERAL
- sql.data.tools.unittesting.tsqleditor
- sql.data.tools.SqlResultsToGridSettingsDlg
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.GENERAL
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.EDITOR_TAB_AND_STATUS_BAR
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.GENERAL
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_RESULTS.RESULTS_TO_TEXT
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_EXECUTION.ANSI
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_EXECUTION.GENERAL
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.ONLINE_EDITING
- VS.TOOLSOPTIONSPAGES.SQL_SERVER_TOOLS.TRANSACT-SQL_EDITOR.QUERY_EXECUTION.ADVANCED
ms.assetid: fa9a250f-7feb-433e-91bd-a09779d74c8b
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e626e50cebf0aba8acde865bfcfd78f1023f978
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094342"
---
# <a name="transact-sql-editor-options"></a>Optionen des Transact-SQL-Editors
Dieses Thema enthält Informationen zu einigen der Optionen des Transact-SQL-Editors. Um diese Optionen festzulegen, navigieren Sie im Menü **Extras\Optionen** zum Dialogfeld **Option**.  
  
[Abfrageausführung](#QueryExecution)  
  
[Abfrageergebnisse](#QueryResults)  
  
## <a name="QueryExecution"></a>Abfrageausführung  
  
|Eigenschaft|und Beschreibung|  
|------------|---------------|  
|**SET ROWCOUNT**|Der Standardwert 0 zeigt an, dass SQL Server so lange auf die Ergebnisse wartet, bis alle Ergebnisse übermittelt sind. Geben Sie einen Wert größer 0 an, wenn die Abfrage von SQL Server nach Übermittlung einer bestimmten Anzahl von Zeilen abgebrochen werden soll. Geben Sie SET ROWCOUNT 0 an, um diese Option zu deaktivieren (sodass alle Zeilen zurückgegeben werden).|  
|**SET TEXTSIZE**|Der Standardwert von 2.147.483.647 Bytes zeigt an, dass SQL Server ein vollständiges Datenfeld bereitstellt, das maximal der Größe von text-, ntext-, nvarchar(max)- und varchar(max)-Datenfeldern entspricht. Dies hat keine Auswirkungen auf den XML-Datentyp. Geben Sie eine kleinere Zahl an, um Ergebnisse mit großen Werten zu beschränken. Spalten, deren Größe die angegebene Zahl übersteigt, werden abgeschnitten.|  
|**Ausführungstimeout**|Gibt die Wartezeit (in Sekunden) an, nach der die Abfrage abgebrochen wird. Der Wert '0' gibt an, dass der Wartevorgang unbegrenzt ist bzw. kein Timeout erfolgt.|  
|**Standardmäßig neue Abfragen im SQLCMD-Modus öffnen**|Aktivieren Sie dieses Kontrollkästchen, um neue Abfragen im SQLCMD-Modus zu öffnen. Dieses Kontrollkästchen ist nur sichtbar, wenn das Dialogfeld über das Menü Extras geöffnet wird.<br /><br />Beachten Sie die folgenden Einschränkungen, wenn Sie diese Option auswählen:<br /><br />– IntelliSense im Abfrage-Editor der Datenbank-Engine ist deaktiviert.<br />– Da der Abfrage-Editor nicht über die Befehlszeile ausgeführt werden kann, ist es nicht möglich, Befehlszeilenparameter, z.B. Variablen, zu übergeben.<br />– Da der Abfrage-Editor nicht auf Anforderungen des Betriebssystems reagieren kann, müssen Sie darauf achten, keine interaktiven Anweisungen auszuführen.|  
|**SET NOCOUNT**|Bewirkt, dass die Meldung bezüglich der Anzahl der von einer Transact-SQL-Anweisung betroffenen Zeilen nicht mit den Ergebnissen zurückgegeben wird. Weitere Informationen finden Sie unter [SET NOCOUNT](http://go.microsoft.com/fwlink/?LinkID=238731).|  
|**SET NOEXEC**|Durch **ON** wird Microsoft® SQL Server™ angewiesen, jeden Batch von Transact-SQL-Anweisungen zu kompilieren, aber nicht auszuführen. Durch **OFF** wird Microsoft® SQL Server™ angewiesen, alle Batches nach der Kompilierung auszuführen. Weitere Informationen finden Sie unter [SET NOEXEC](http://go.microsoft.com/fwlink/?LinkId=238770).|  
|**SET PARSEONLY**|Überprüft die Syntax jeder Transact-SQL-Anweisung und gibt Fehlermeldungen zurück, ohne die Anweisung zu kompilieren oder auszuführen. Weitere Informationen finden Sie unter [SET PARSEONLY](http://go.microsoft.com/fwlink/?LinkId=238734).|  
|**SET CONCAT_NULL_YIELDS_NULL**|Steuert die Behandlung von Verkettungsergebnissen als NULL-Werte oder als leere Zeichenfolgenwerte. Weitere Informationen finden Sie unter [SET CONCAT_NULL_YIELDS_NULL](http://go.microsoft.com/fwlink/?LinkId=238733).|  
|**SET ARITHABORT**|Beendet eine Abfrage, wenn während der Abfrage ein Überlauffehler oder ein Fehler aufgrund einer Division durch Null auftritt. Weitere Informationen finden Sie unter  [SET ARITHABORT](http://msdn.microsoft.com/en-us/library/aa259212(v=SQL.80).aspx).|  
|**SET SHOWPLAN_TEXT**|Bewirkt, dass Transact-SQL-Anweisungen von Microsoft® SQL Server™ nicht ausgeführt werden. Stattdessen gibt SQL Server detaillierte Informationen zur Ausführung der Anweisungen zurück. Weitere Informationen finden Sie unter [SET SHOWPLAN_TEXT](http://go.microsoft.com/fwlink/?LinkID=238737).|  
|**SET STATISTICS TIME**|Zeigt an, wie viele Millisekunden zum Analysieren, Kompilieren und Ausführen jeder Anweisung benötigt wurden.|  
|**SET STATISTICS IO**|Bewirkt, dass Microsoft® SQL Server™ Informationen zum Umfang der Datenträgeraktivitäten anzeigt, die durch Transact-SQL-Anweisungen generiert werden.|  
|**SET TRANSACTION ISOLATION LEVEL**|Steuert das standardmäßige Transaktionssperrverhalten für alle **SELECT** -Anweisungen von Microsoft® SQL Server™, die von einer Verbindung ausgestellt wurden. Weitere Informationen finden Sie unter  [SET TRANSACTION ISOLATION LEVEL](http://go.microsoft.com/fwlink/?LinkId=238730).|  
|**SET LOCK_TIMEOUT**|Gibt an, wie viele Millisekunden eine Anweisung auf die Aufhebung einer Sperre wartet. Weitere Informationen finden Sie unter [SET LOCK_TIMEOUT](http://go.microsoft.com/fwlink/?LinkId=238747).|  
|**SET QUERY_GOVERNOR_COST_LIMIT**|Überschreibt den zurzeit konfigurierten Wert für die aktuelle Verbindung. Weitere Informationen finden Sie unter [SET QUERY_GOVERNOR_COST_LIMIT](http://go.microsoft.com/fwlink/?LinkId=238749).|  
|**SET ANSI_DEFAULTS**|Steuert eine Gruppe von Microsoft® SQL Server™-Einstellungen, durch die einige SQL-92-Standardverhaltensweisen zusammenfassend festgelegt werden. Weitere Informationen finden Sie unter [SET ANSI_DEFAULTS](http://go.microsoft.com/fwlink/?LinkId=238750).|  
|**SET QUOTED_IDENTIFIER**|Bewirkt, dass Microsoft® SQL Server™ die SQL-92-Regeln für das Setzen von Anführungszeichen als Trennzeichen bei Bezeichnern und Literalzeichenfolgen befolgt. Bei Bezeichnern, die von doppelten Anführungszeichen begrenzt werden, kann es sich um reservierte Transact-SQL-Schlüsselwörter oder um Zeichen handeln, die nach den Transact-SQL-Syntaxregeln für Bezeichner eigentlich nicht zulässig sind. Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER](http://go.microsoft.com/fwlink/?LinkId=238751).|  
|**SET ANSI_NULL_DFLT_ON**|Ändert das Sitzungsverhalten, sodass die Standardeinstellung der NULL-Zulässigkeit für neue Spalten überschrieben wird, wenn die Option „ANSI NULL Default“ für die Datenbank auf FALSE festgelegt ist. Weitere Informationen finden Sie unter [SET ANSI_NULL_DFLT_ON](http://go.microsoft.com/fwlink/?LinkID=238752).|  
|**SET IMPLICIT_TRANSACTIONS**|Durch **ON**wird der implizite Transaktionsmodus für die Verbindung festgelegt. Bei **OFF**wechselt die Verbindung wieder in den Autocommit-Transaktionsmodus. Weitere Informationen finden Sie unter [SET IMPLICIT_TRANSACTIONS](http://go.microsoft.com/fwlink/?LinkId=238753).|  
|**SET CURSOR_CLOSE_ON_COMMIT**|Steuert, ob ein Cursor beim Commit für eine Transaktion geschlossen wird oder nicht. Weitere Informationen finden Sie unter [SET CURSOR_CLOSE_ON_COMMIT](http://go.microsoft.com/fwlink/?LinkId=238754).|  
|**SET ANSI_PADDING**|Steuert das Speichern von Werten in der Spalte, wenn die Werte kürzer als die definierte Spaltengröße sind, sowie das Speichern von Werten mit nachfolgenden Leerzeichen in Daten vom Typ **char**, **varchar**, **binary**und **varbinary** . Weitere Informationen finden Sie unter [SET ANSI_PADDING](http://go.microsoft.com/fwlink/?LinkId=238755).|  
|**SET ANSI_WARNINGS**|Gibt das SQL-92-Standardverhalten für verschiedene Fehlerbedingungen an. Weitere Informationen finden Sie unter [SET ANSI_WARNINGS](http://go.microsoft.com/fwlink/?LinkId=238758).|  
|**SET ANSI_NULLS**|Gibt das SQL-92-kompatible Verhalten für den Gleichheits- (**=**) und den Ungleichheits-Vergleichsoperator (**<>**) bei Verwendung von NULL-Werten an. Weitere Informationen finden Sie unter [SET ANSI_NULLS](http://go.microsoft.com/fwlink/?LinkId=238759).|  
  
## <a name="QueryResults"></a>Abfrageergebnisse  
  
|Eigenschaft|und Beschreibung|  
|------------|---------------|  
|**Abfrage in das Resultset einschließen**|Gibt den Text der Abfrage als Teil des Resultsets zurück.|  
|**Spaltenheader beim Kopieren oder Speichern der Ergebnisse einschließen**|Schließt Spaltenheader (Titel) ein, wenn Ergebnisse in die Zwischenablage kopiert oder in einer Datei gespeichert werden. Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nur die Ergebnisdaten und nicht die Spaltenheader speichern oder kopieren möchten.|  
|**Ergebnisse nach der Ausführung verwerfen**|Gibt Arbeitsspeicher frei, indem die Abfrageergebnisse nach der Anzeige auf dem Bildschirm verworfen werden.|  
|**Ergebnisse auf separater Registerkarte anzeigen**|Zeigt das Resultset statt unten im Dokumentfenster der Abfrage in einem neuen Dokumentfenster an.|  
|**Nach Ausführung der Abfrage zur Ergebnisregisterkarte wechseln**|Verschiebt den Fokus automatisch auf das Resultset.|  
|**Maximale Anzahl von abgerufenen Zeichen**|Nicht-XML-Daten:<br /><br />Geben Sie eine Zahl zwischen 1 und 65.535 ein, um die maximale Anzahl der in einer Zelle angezeigten Zeichen anzugeben. **Hinweis:** Wenn Sie eine große Anzahl von Zeichen angeben, werden die Daten im Resultset unter Umständen abgeschnitten angezeigt. Die maximale Anzahl der pro Zelle angezeigten Zeichen ist von der Schriftgröße abhängig. Wenn große Resultsets zurückgegeben werden, kann ein großer Wert in diesem Feld dazu führen, dass SQL Server Management Studio viel Arbeitsspeicher beansprucht und die Systemleistung beeinträchtigt.<br /><br />XML-Daten:<br /><br />Wählen Sie 1 MB, 2 MB oder 5 MB aus. Wählen Sie „Unbegrenzt“ aus, um alle Zeichen abzurufen.|  
|**Ausgabeformat**|Standardmäßig werden die Ausgaben in Spalten angezeigt, die durch Auffüllen der Ergebnisse mit Leerstellen erstellt werden. Als weitere Optionen können Kommas, Tabstopps oder Leerzeichen zur Trennung der Spalten gewählt werden. Aktivieren Sie das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** , um im Feld **Benutzerdefiniertes Trennzeichen** ein anderes Trennzeichen festzulegen.|  
|**Benutzerdefiniertes Trennzeichen**|Geben Sie das gewünschte Zeichen zum Trennen der Spalten an. Diese Option ist nur verfügbar, wenn im Feld **Ausgabeformat** das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** aktiviert wurde.|  
|**Spaltenheader im Resultset einschließen**|Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nicht möchten, dass jede Spalte mit einem Spaltentitel versehen wird.|  
|**Durchführen eines Bildlaufs beim Empfangen von Ergebnissen**|Aktivieren Sie dieses Kontrollkästchen, wenn zuerst die zuletzt zurückgegebenen Datensätze am unteren Ende der Ergebnisliste angezeigt werden sollen. Deaktivieren Sie dieses Kontrollkästchen, wenn zunächst die ersten empfangenen Zeilen angezeigt werden sollen.|  
|**Numerische Werte rechts ausrichten**|Aktivieren Sie dieses Kontrollkästchen, um numerische Werte an der Spalte rechts auszurichten. Diese Option kann die Überprüfung von Zahlen mit einer festen Anzahl von Dezimalstellen erleichtern.|  
|**Ergebnisse nach der Ausführung der Abfrage verwerfen**|Gibt Arbeitsspeicher frei, indem die Abfrageergebnisse nach der Anzeige auf dem Bildschirm verworfen werden.|  
|**Ergebnisse auf separater Registerkarte anzeigen**|Aktivieren Sie dieses Kontrollkästchen, um das Resultset in einem neuen Dokumentfenster anzuzeigen anstatt im unteren Bereich des Dokumentfensters der Abfrage.|  
|**Nach Ausführung der Abfrage zur Ergebnisregisterkarte wechseln**|Aktivieren Sie dieses Kontrollkästchen, wenn der Fokus automatisch auf das Resultset verschoben werden soll.|  
|**Pro Spalte angezeigte maximale Anzahl von Zeichen**|Dieser Wert liegt standardmäßig bei 256. Erhöhen Sie diesen Wert, wenn Sie größere Resultsets ohne Kürzungen anzeigen möchten.|  
|**Standard wiederherstellen**|Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.|  
  
