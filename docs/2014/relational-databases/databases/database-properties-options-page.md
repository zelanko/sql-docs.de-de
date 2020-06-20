---
title: Datenbankeigenschaften (Seite Optionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.options.f1
ms.assetid: a3447987-5507-4630-ac35-58821b72354d
author: stevestein
ms.author: sstein
ms.openlocfilehash: e856e820719054ad1f01fe0e0306aa278d62ec2c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970140"
---
# <a name="database-properties-options-page"></a>Datenbankeigenschaften (Seite Optionen)
  Mithilfe dieser Seite können Sie Optionen für die ausgewählte Datenbank anzeigen und ändern. Weitere Informationen zu den auf dieser Seite verfügbaren Optionen finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="page-header"></a>Seitenheader  
 **Sortierung**  
 Geben Sie die Sortierung der Datenbank durch eine Auswahl aus der Liste an. Weitere Informationen finden Sie unter [Festlegen oder Ändern der Datenbanksortierung](../collations/set-or-change-the-database-collation.md).  
  
 **Wiederherstellungsmodell**  
 Geben Sie eines der folgenden Modelle für die Wiederherstellung der Datenbank an: **Vollständig**, **Massenprotokolliert**oder **Einfach**. Weitere Informationen zu Wiederherstellungsmodellen finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).  
  
 **Kompatibilitätsgrad**  
 Geben Sie die letzte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, die von der Datenbank unterstützt wird. Mögliche Werte sind  **SQL Server 2014 (120)**,  **SQL Server 2012 (110)** und **SQL Server 2008 (100)**. Wenn eine SQL Server 2005-Datenbank auf SQL Server 2014 aktualisiert wird, wird der Kompatibilitätsgrad für die Datenbank von 90 in 100 geändert.  Der Kompatibilitätsgrad 90 wird in SQL Server 2014 nicht unterstützt. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **Einschlusstyp**  
 Geben Sie Kein oder Teilweise an, um festzulegen, ob es sich um eine eigenständige Datenbank handelt. Weitere Informationen zu eigenständigen Datenbanken finden Sie unter [Eigenständige Datenbanken](contained-databases.md). Die Servereigenschaft **Eigenständige Datenbanken aktivieren** muss auf **TRUE** festgelegt werden, bevor eine Datenbank als eigenständige Datenbank konfiguriert werden kann.  
  
> [!IMPORTANT]  
>  Das Aktivieren von teilweise eigenständigen Datenbanken delegiert die Steuerung über den Zugriff auf die Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an die Besitzer der Datenbank. Weitere Informationen finden Sie unter [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).  
  
## <a name="automatic"></a>Automatisch  
 **Automatisch schließen**  
 Gibt an, ob die Datenbank ordnungsgemäß heruntergefahren wird und Ressourcen freigegeben werden, nachdem der letzte Benutzer die Anwendung beendet hat. Mögliche Werte sind `True` und `False`. Bei `True` wird die Datenbank heruntergefahren, und die Ressourcen werden freigegeben, wenn sich der letzte Benutzer abgemeldet hat.  
  
 Inkrementelle Statistiken automatisch erstellen  
 Gibt an, ob die Option INCREMENTAL beim Erstellen von Statistiken für einzelne Partitionen verwendet werden soll. Weitere Informationen zu inkrementellen Statistiken finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Statistiken automatisch erstellen**  
 Gibt an, ob die Datenbank fehlende Optimierungsstatistiken automatisch erstellt. Mögliche Werte sind `True` und `False`. Bei `True` werden fehlende Statistiken, die von einer Abfrage zur Optimierung benötigt werden, automatisch während der Optimierung erstellt. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Automatisch verkleinern**  
 Gibt an, ob die Datenbankdateien für eine regelmäßige Verkleinerung verfügbar sind. Mögliche Werte sind `True` und `False`. Weitere Informationen finden Sie unter [Verkleinern einer Datenbank](shrink-a-database.md).  
  
 **Statistiken automatisch aktualisieren**  
 Gibt an, ob die für die Datenbank veralteten Optimierungsstatistiken automatisch aktualisiert werden. Mögliche Werte sind `True` und `False`. Bei `True` werden veraltete Statistiken, die von einer Abfrage zur Optimierung benötigt werden, automatisch während der Optimierung aktualisiert. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Statistiken automatisch asynchron aktualisieren**  
 Bei `True` werden Abfragen, die ein automatisches Update veralteter Statistiken initiieren, vor dem Kompilieren nicht darauf warten, dass die Statistiken aktualisiert werden. Nachfolgende Abfragen verwenden die aktualisierten Statistiken, sobald diese verfügbar sind.  
  
 Wenn `False` Abfragen, die ein automatisches Update veralteter Statistiken initiieren, warten Sie, bis die aktualisierten Statistiken im Abfrage Optimierungs Plan verwendet werden können.  
  
 Wenn diese Option auf fest `True` gelegt wird, hat dies keine Auswirkungen, es sei denn, die Statistiken für die **Automatische Aktualisierung** `True`  
  
## <a name="containment"></a>Containment  
 In eigenständigen Datenbanken können einige Einstellungen, die normalerweise auf Serverebene konfiguriert werden, auf Datenbankebene konfiguriert werden.  
  
 **LCID der Volltext-Standardsprache**  
 Gibt eine Standardsprache für Spalten mit Volltextindex an. Linguistische Analysen von Daten mit Volltextindex werden von der Sprache der Daten bestimmt. Der Standardwert für diese Option ist die Sprache des Servers. Informationen zu der Sprache, die der angezeigten Einstellung entspricht, finden Sie unter [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
 **Standardsprache**  
 Die Standardsprache für alle neuen Benutzer eigenständiger Datenbanken, sofern nicht anders angegeben.  
  
 **Geschachtelte Trigger aktiviert**  
 Ermöglicht Triggern, weitere Trigger auszulösen. Trigger können maximal 32 Ebenen tief geschachtelt werden. Weitere Informationen finden Sie im Abschnitt „Geschachtelte Trigger“ unter [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Füll Wörter transformieren**  
 Unterdrückt eine Fehlermeldung, wenn Füllwörter (d. h. Stoppwörter) bewirken, dass eine boolesche Operation für eine Volltextabfrage 0 (null) Zeilen zurückgibt. Weitere Informationen finden Sie unter [Füllwörtertransformation (Serverkonfigurationsoption)](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).  
  
 **Umstellungsjahr für Angaben mit zwei Ziffern**  
 Gibt die höchste Zahl an, die als eine zweistellige Jahresangabe eingegeben werden kann. Das aufgeführte Jahr und die vorherigen 99 Jahre können als eine zweistellige Jahresangabe eingegeben werden. Alle anderen Jahre müssen als eine vierstellige Jahresangabe eingegeben werden.  
  
 Die Standardeinstellung 2049 zeigt beispielsweise an, dass ein als '3/14/49' eingegebenes Datum als 14. März 2049 und ein als '3/14/50' eingegebenes Datum als 14. März 1950 interpretiert wird. Weitere Informationen [Konfigurieren der Serverkonfigurationsoption Umstellungsjahr für Angaben mit zwei Ziffern](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
## <a name="cursor"></a>Cursor  
 **Schließen des Cursors nach Commit aktiviert**  
 Gibt an, ob der Cursor geschlossen wird, nachdem für die den Cursor öffnende Transaktion ein Commit durchgeführt wurde. Mögliche Werte sind `True` und `False`. Bei `True` werden alle Cursor geschlossen, die geöffnet sind, wenn für eine Transaktion ein Commit oder ein Rollback ausgeführt wird. Bei `False` bleiben diese Cursor geöffnet, wenn für eine Transaktion ein Commit ausgeführt wird. Bei `False` werden beim Rollback einer Transaktion alle außer den als INSENSITIVE oder STATIC definierten Cursorn geschlossen. Weitere Informationen finden Sie unter [SET CURSOR_CLOSE_ON_COMMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-cursor-close-on-commit-transact-sql).  
  
 **Standardcursor**  
 Gibt das Verhalten für Standardcursor an. Bei `True` werden Cursordeklarationen standardmäßig auf LOCAL festgelegt. Wenn `False` , werden- [!INCLUDE[tsql](../../includes/tsql-md.md)] Cursor standardmäßig auf Global eingestellt.  
  
## <a name="filestream"></a>FILESTREAM  
 **FILESTREAM-Verzeichnisname**  
 Geben Sie den Verzeichnisnamen für die FILESTREAM-Daten an, die der ausgewählten Datenbank zugeordnet sind.  
  
 **Nicht transaktionsgebundener FILESTREAM-Zugriff**  
 Geben Sie eine der folgenden Optionen für nicht transaktionalen Zugriff über das Dateisystem auf FILESTREAM-Daten an, die in FileTables gespeichert sind: **OFF**, **READ_ONLY**oder **FULL**. Wenn FILESTREAM nicht auf dem Server aktiviert ist, wird dieser Wert auf OFF festgelegt und deaktiviert. Weitere Informationen finden Sie unter [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).  
  
## <a name="miscellaneous"></a>Verschiedenes  
 **ANSI NULL Default**  
 Lässt NULL-Werte für alle benutzerdefinierten Datentypen oder Spalten zu, die während einer `NOT NULL`-Anweisung oder `CREATE TABLE`-Anweisung nicht explizit als `ALTER TABLE` definiert wurden (Standardstatus). Weitere Informationen finden Sie unter [SET ANSI_NULL_DFLT_ON &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-null-dflt-on-transact-sql) und [SET ANSI_NULL_DFLT_OFF &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-null-dflt-off-transact-sql).  
  
 **ANSI NULLS aktiviert**  
 Gibt das Verhalten der Vergleichsoperatoren Gleich (`=`) und Ungleich (`<>`) bei Verwendung mit NULL-Werten an. Mögliche Werte sind `True` (on) und `False` (Off). Bei `True` ergeben alle Vergleiche mit einem Nullwert UNKNOWN. Bei `False` werden Vergleiche von nicht-Unicode-Werten mit einem NULL-Wert als ausgewertet, `True` Wenn beide Werte NULL sind. Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).  
  
 **ANSI-Auffüllung aktiviert**  
 Gibt an, ob die ANSI-Auffüllung aktiviert ist. Zulässige Werte sind `True` (on) und `False` (Off). Weitere Informationen finden Sie unter [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **ANSI-Warnungen aktiviert**  
 Gibt das ISO-Standardverhalten für verschiedene Fehlerbedingungen an. Wenn der `True` Wert ist, wird eine Warnmeldung generiert, wenn NULL-Werte in Aggregatfunktionen (z. b. Sum, AVG, Max, min, STDEV, STDEVP, var, VarP oder count) vorkommen. Wenn `False` , wird keine Warnung ausgegeben. Weitere Informationen finden Sie unter [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).  
  
 **Abbruch bei arithmetischem Fehler aktiviert**  
 Gibt an, ob die Datenbankoption für den Abbruch bei arithmetischem Fehler aktiviert ist. Mögliche Werte sind `True` und `False`. Bei `True` bewirkt ein Überlauffehler oder ein Fehler aufgrund einer Division durch Null, dass die Abfrage oder der Batch beendet wird. Tritt der Fehler in einer Transaktion auf, so wird für die Transaktion ein Rollback durchgeführt. Bei `False` wird eine Warnmeldung angezeigt, aber die Abfrage, der Batch oder die Transaktion werden fortgesetzt, als wäre kein Fehler aufgetreten. Weitere Informationen finden Sie unter [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).  
  
 **Verketten von NULL-Werten ergibt NULL**  
 Gibt das Verhalten an, wenn NULL-Werte verkettet werden. Wenn der-Eigenschafts Wert ist `True` , `string` gibt + NULL NULL zurück. Wenn `False` der Wert ist, ist das Ergebnis `string` . Weitere Informationen finden Sie unter [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).  
  
 **Datenbankübergreifende Besitzverkettung aktiviert**  
 Dieser schreibgeschützte Wert gibt an, ob die datenbankübergreifende Besitzverkettung aktiviert wurde. Bei `True` kann es sich bei der Datenbank um die Quelle oder das Ziel einer datenbankübergreifenden Besitz Kette handeln. Verwenden Sie die ALTER DATABASE-Anweisung, um diese Eigenschaft festzulegen.  
  
 **Datumskorrelationsoptimierung aktiviert**  
 Wenn `True` der Wert ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet Korrelations Statistiken zwischen zwei beliebigen Tabellen in der Datenbank, die durch eine FOREIGN KEY-Einschränkung verknüpft sind und über `datetime` Spalten verfügen.  
  
 Bei `False` werden Korrelations Statistiken nicht beibehalten.  
  
 **Abbruch bei numerischem Runden**  
 Gibt an, wie Rundungsfehler in der Datenbank behandelt werden. Mögliche Werte sind `True` und `False`. Bei `True` wird ein Fehler generiert, wenn ein Genauigkeitsverlust in einem Ausdruck auftritt. Wenn `False` , werden bei Genauigkeits Verlusten keine Fehlermeldungen generiert, und das Ergebnis wird auf die Genauigkeit der Spalte oder Variablen gerundet, die das Ergebnis speichert. Weitere Informationen finden Sie unter [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).  
  
 **Parametrisierung**  
 Bei **SIMPLE**werden Abfragen basierend auf dem Standardverhalten der Datenbank parametrisiert. Bei **erzwungener** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Parametrisierung werden alle Abfragen in der Datenbank parametrisiert.  
  
 **Bezeichner in Anführungszeichen aktiviert**  
 Gibt an, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Schlüsselwörter als Bezeichner (Objekt- oder Variablennamen) verwendet werden können, wenn sie in Anführungszeichen eingeschlossen sind. Mögliche Werte sind `True` und `False`. Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **Rekursive Trigger aktiviert**  
 Gibt an, ob Trigger von anderen Triggern ausgelöst werden können. Mögliche Werte sind `True` und `False`. Wenn Sie auf festgelegt `True` ist, ermöglicht dies das rekursive Auslösen von Triggern. Wenn Sie auf festgelegt ist `False` , wird nur die direkte Rekursion verhindert. Um die indirekte Rekursion zu deaktivieren, legen Sie mithilfe von sp_configure auch die Serveroption Geschachtelte Trigger auf 0 fest. Weitere Informationen finden Sie unter [Erstellen von geschachtelten Triggern](../triggers/create-nested-triggers.md).  
  
 `Trustworthy`  
 Wenn `True` diese Option angezeigt wird, gibt diese schreibgeschützte Option an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Zugriff auf Ressourcen außerhalb der Datenbank in einem in der Datenbank eingerichteten Identitätswechsel Kontext zulässt. Identitätswechselkontexte können innerhalb der Datenbank mithilfe der EXECUTE AS USER-Anweisung oder der EXECUTE AS-Klausel für Datenbankmodule eingerichtet werden.  
  
 Der Besitzer der Datenbank benötigt außerdem die AUTHENTICATE SERVER-Berechtigung auf Serverebene, um Zugriff zu erhalten.  
  
 Diese Eigenschaft ermöglicht zudem die Erstellung und Ausführung von unsicheren Assemblys und Assemblys mit externem Zugriff innerhalb der Datenbank. Zusätzlich zum Festlegen dieser Eigenschaft auf `True` benötigt der Besitzer der Datenbank die Berechtigungen EXTERNAL ACCESS ASSEMBLY oder UNSAFE ASSEMBLY auf Serverebene.  
  
 Standardmäßig ist diese Eigenschaft für alle Benutzer Datenbanken und alle System Datenbanken (mit Ausnahme von **msdb**) auf festgelegt `False` . Der Wert kann für die **Model** -und **tempdb** -Datenbanken nicht geändert werden.  
  
 TRUSTWORTHY wird auf `False` festgelegt, wenn eine Datenbank an den Server angefügt wird.  
  
 Die empfohlene Vorgehensweise zum Zugreifen auf Ressourcen außerhalb der Datenbank unter einem Identitätswechselkontext ist die Verwendung von Zertifikaten und Signaturen statt der Option `Trustworthy`.  
  
 Verwenden Sie zum Festlegen dieser Eigenschaft die ALTER DATABASE-Anweisung.  
  
 **VarDecimal-Speicherformat ist aktiviert**  
 Diese Option ist ab und höheren Versionen schreibgeschützt [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . alle Datenbanken sind für das vardecimal--Speicherformat aktiviert. Diese Option verwendet [sp_db_vardecimal_storage_format](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
## <a name="recovery"></a>Wiederherstellung  
 **Seitenüberprüfung**  
 Gibt die Option an, die verwendet wird, um unvollständige E/A-Transaktionen zu entdecken und zu melden, die durch Datenträger-E/A-Fehler verursacht wurden. Mögliche Werte sind **None**, **TornPageDetection** und **Checksum**. Weitere Informationen finden Sie unter [Verwalten der suspect_pages-Tabelle &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)wiederhergestellt werden.  
  
 **Wiederherstellungszeit für das Ziel (Sekunden)**  
 Gibt die maximale Grenze für die Zeit in Sekunden an, die für die Wiederherstellung der angegebenen Datenbank im Fall eines Fehlers aufgewendet wird. Weitere Informationen finden Sie unter [Datenbankprüfpunkte &#40;SQL Server&#41;](../logs/database-checkpoints-sql-server.md).  
  
## <a name="state"></a>State  
 **Datenbank schreibgeschützt**  
 Gibt an, ob die Datenbank schreibgeschützt ist. Mögliche Werte sind `True` und `False`. Bei `True` können Benutzer die Daten in der Datenbank nur lesen. Die Benutzer können keine Daten oder Datenbankobjekte ändern. Die Datenbank selbst kann jedoch mithilfe der DROP DATABASE-Anweisung gelöscht werden. Die Datenbank darf nicht verwendet werden, wenn ein neuer Wert für die Option **Datenbank schreibgeschützt** angegeben wird. Die master-Datenbank stellt eine Ausnahme dar, und nur der Systemadministrator darf die master-Datenbank verwenden, während die Option festgelegt wird.  
  
 **Datenbankstatus**  
 Zeigt den aktuellen Status der Datenbank an. Sie kann nicht bearbeitet werden. Weitere Informationen zum **Datenbankstatus**finden Sie unter [Datenbankstatus](database-states.md).  
  
 **Zugriff einschränken**  
 Gibt an, welche Benutzer auf die Datenbank zugreifen können. Mögliche Werte:  
  
-   **Mehrere**  
  
     Dieser normale Status für eine Produktionsdatenbank ermöglicht mehreren Benutzern, gleichzeitig auf die Datenbank zuzugreifen.  
  
-   **Single**  
  
     Wird für Wartungsaktionen verwendet. Nur ein Benutzer kann zu einem Zeitpunkt auf die Datenbank zugreifen.  
  
-   **Eingeschränkt**  
  
     Nur Mitglieder der Rollen db_owner, dbcreator oder sysadmin können die Datenbank verwenden.  
  
 **Verschlüsselung aktiviert**  
 `True`Gibt an, dass diese Datenbank für die Datenbankverschlüsselung aktiviert ist. Für die Verschlüsselung ist ein Verschlüsselungsschlüssel für eine Datenbank erforderlich. Weitere Informationen finden Sie unter [Transparente Datenverschlüsselung &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
