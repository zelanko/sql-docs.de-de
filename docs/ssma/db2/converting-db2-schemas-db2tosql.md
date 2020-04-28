---
title: Umstellen von DB2-Schemas (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7947efc3-ca86-4ec5-87ce-7603059c75a0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7a16a28a163acece321cc2229e9988cf7ab01f9e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67989867"
---
# <a name="converting-db2-schemas-db2tosql"></a>Umstellen von DB2-Schemas (DB2ToSQL)
Nachdem Sie eine Verbindung mit DB2 hergestellt, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindung mit hergestellt und Projekt-und Daten Zuordnungsoptionen festgelegt haben, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie DB2-Datenbankobjekte in Datenbankobjekte konvertieren.  
  
## <a name="the-conversion-process"></a>Der Konvertierungsprozess  
Das Konvertieren von Datenbankobjekten übernimmt die Objekt Definitionen aus DB2, konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie in ähnliche Objekte und lädt diese Informationen dann in die SSMA-Metadaten. Die Informationen werden nicht in die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen. Anschließend können Sie die Objekte und deren Eigenschaften mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer anzeigen.  
  
Während der Konvertierung druckt SSMA Ausgabemeldungen im Ausgabebereich und Fehlermeldungen in den Fehlerliste Bereich. Bestimmen Sie anhand der Ausgabe-und Fehlerinformationen, ob Sie die DB2-Datenbanken oder den Konvertierungsprozess ändern müssen, um die gewünschten Konvertierungs Ergebnisse zu erhalten.  
  
## <a name="setting-conversion-options"></a>Festlegen von Konvertierungsoptionen  
Überprüfen Sie vor dem Konvertieren von Objekten die Projekt Konvertierungsoptionen im Dialogfeld **Projekteinstellungen** . Mit diesem Dialogfeld können Sie festlegen, wie SSMA Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
## <a name="conversion-results"></a>Konvertierungs Ergebnisse  
Die folgende Tabelle zeigt, welche DB2-Objekte konvertiert werden, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die resultierenden Objekte:  
  
|DB2-Objekte|Resultierende SQL Server Objekte|  
|-----------|----------------------------|  
|Datentypen|**SSMA ordnet alle Typen außer den folgenden Angaben zu:**<br /><br />CLOB: einige Native Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. b. CLOB_EMPTY ()).<br /><br />BLOB: einige Native Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. b. BLOB_EMPTY ()).<br /><br />Dblob: einige Native Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. b. DBLOB_EMPTY ()).|  
|Benutzerdefinierte Typen|**SSMA ordnet den folgenden benutzerdefinierten zu:**<br /><br />Eindeutiger Typ<br /><br />Strukturierter Typ<br /><br />SQL pl-Datentypen: Beachten Sie, dass der schwache Cursortyp nicht unterstützt wird.|  
|Sonderregister|**SSMA ordnet nur die unten aufgeführten Register zu:**<br /><br />Aktueller Zeitstempel<br /><br />Aktuelles Datum<br /><br />aktuelle Uhrzeit<br /><br />aktuelle Zeitzone<br /><br />Aktueller Benutzer<br /><br />SESSION_USER und Benutzer<br /><br />SYSTEM_USER<br /><br />aktuelle CLIENT_APPLNAME<br /><br />aktuelle CLIENT_WRKSTNNAME<br /><br />Aktuelles Sperr Timeout<br /><br />Aktuelles Schema<br /><br />aktueller Server<br /><br />aktuelle Isolation<br /><br />Andere spezielle Register sind nicht der Semantik von SQL Server zugeordnet.|  
|CREATE TABLE|**SSMA ordnet CREATE TABLE mit den folgenden Ausnahmen zu:**<br /><br />Multidimensionale Clustering-Tabellen (MDC)<br /><br />Range-Clustered Tables (RCT)<br /><br />Partitionierte Tabellen<br /><br />Getrennte Tabelle<br /><br />Data Capture-Klausel<br /><br />Implizit verborgene Option<br /><br />VOLATILE-Option|  
|CREATE VIEW|SSMA Maps Create View mit der Option with local Check Option, andere Optionen werden jedoch nicht der SQL Server-Semantik zugeordnet.|  
|CREATE INDEX|**SSMA Maps Create Index mit den folgenden Ausnahmen:**<br /><br />XML-Index<br /><br />BUSINESS_TIME ohne Überschneidungen (Option)<br /><br />Partitionierte Klausel<br /><br />Option nur für Spezifikation<br /><br />Option "erweitern mit"<br /><br />Minpctused (Option)<br /><br />Seiten Teilung (Option)|  
|Trigger|**SSMA ordnet die folgende auslösersemantik zu:**<br /><br />After/for each-Zeilen Trigger<br /><br />After/for each-Anweisung auslösen<br /><br />Vor/für jede Zeile und anstelle von/für jeden Zeilen Trigger|  
|Sequenzen|Sind zugeordnet.|  
|SELECT-Anweisung|**SSMA Maps wählen Sie mit den folgenden Ausnahmen aus:**<br /><br />Data-Change-Table-Reference-Klausel: teilweise zugeordnet, aber endgültige Tabellen werden nicht unterstützt.<br /><br />Tabellen Verweis Klausel: teilweise zugeordnet, aber nur-Table-Reference, Outer-Table-Reference, analyze_table-Expression, Collection-abgeleitete Tabelle, XMLTable-Expression ist nicht der SQL Server-Semantik zugeordnet.<br /><br />Die Period-Specification-Klausel ist nicht zugeordnet.<br /><br />Die Continue-Handler-Klausel ist nicht zugeordnet.<br /><br />Die typisierte Korrelations Klausel ist nicht zugeordnet.<br /><br />Die Klausel für die gleichzeitige Zugriffs Auflösung ist nicht zugeordnet.|  
|Values-Anweisung|Wird zugeordnet.|  
|INSERT-Anweisung|Wird zugeordnet.|  
|Update-Anweisung|S**SMA ordnet Updates mit den folgenden Ausnahmen zu:**<br /><br />Table-Reference-Klausel-only: der Tabellen Verweis ist nicht der SQL Server-Semantik zugeordnet.<br /><br />Period-Klausel-ist nicht zugeordnet.|  
|MERGE-Anweisung|**SSMA ordnet die Zusammenführung mit den folgenden Ausnahmen zu:**<br /><br />Einzelne im Vergleich zu mehreren Vorkommen jeder Klausel: wird der SQL Server-Semantik für begrenzte Vorkommen der einzelnen Klauseln zugeordnet.<br /><br />Signal-Klausel-nicht SQL Server Semantik zugeordnet<br /><br />Gemischte Update-und DELETE-Klauseln: SQL Server Semantik nicht zugeordnet<br /><br />Period-clause: wird nicht SQL Server Semantik zugeordnet.|  
|DELETE-Anweisung|**SSMA ordnet DELETE mit den folgenden Ausnahmen zu:**<br /><br />Table-Reference-Klausel-only: der Tabellen Verweis ist nicht der SQL Server-Semantik zugeordnet.<br /><br />Period-Klausel-wird nicht SQL Server Semantik zugeordnet|  
|Isolationsstufe und Sperrentyp|Wird zugeordnet.|  
|Prozeduren (SQL)|Sind zugeordnet.|  
|Prozeduren (extern)|Manuelle Aktualisierung erforderlich.|  
|Prozeduren (Source)|Nicht SQL Server Semantik zugeordnet werden.|  
|Zuweisungsanweisung|Wird zugeordnet.|  
|Callananweisung für eine Prozedur|Wird zugeordnet.|  
|CASE-Anweisung|Wird zugeordnet.|  
|FOR-Anweisung|Wird zugeordnet.|  
|GOTO-Anweisung|Wird zugeordnet.|  
|IF-Anweisung|Wird zugeordnet.|  
|ITERATE-Anweisung|Wird zugeordnet.|  
|Leave-Anweisung|Wird zugeordnet.|  
|Loop-Anweisung|Wird zugeordnet.|  
|REPEAT-Anweisung|Wird zugeordnet.|  
|RESIGNAL-Anweisung|Bedingungen werden nicht unterstützt. Nachrichten können optional sein.|  
|Return-Anweisung|Wird zugeordnet.|  
|Signal-Anweisung|Bedingungen werden nicht unterstützt. Nachrichten können optional sein.|  
|While-Anweisung|Wird zugeordnet.|  
|Get Diagnostics-Anweisung|**SSMA ordnet die Diagnose mit den folgenden Ausnahmen zu:**<br /><br />Row_count-ist zugeordnet.<br /><br />DB2_RETURN_STATUS-ist zugeordnet.<br /><br />MESSAGE_TEXT-ist zugeordnet.<br /><br />DB2_SQL_NESTING_LEVEL-keine Zuordnung zu SQL Server Semantik<br /><br />DB2_TOKEN_STRING-keine Zuordnung zu SQL Server Semantik|  
|Cursor|**SSMA ordnet Cursor mit den folgenden Ausnahmen zu:**<br /><br />Anweisung zum Zuordnen von Cursorn-entspricht nicht SQL Server Semantik<br /><br />Zuordnung der Locators-Anweisung-entspricht nicht SQL Server Semantik<br /><br />DECLARE CURSOR-Anweisung: die returnability-Klausel ist nicht der SQL Server-Semantik zugeordnet.<br /><br />FETCH-Anweisung-partielle Zuordnung. Variablen als Ziel werden nur unterstützt. Der SQLDA-Deskriptor ist nicht der SQL Server-Semantik zugeordnet.|  
|Variables|Sind zugeordnet.|  
|Ausnahmen, Handler und Bedingungen|**SSMA ordnet die "Ausnahmebehandlung" mit den folgenden Ausnahmen zu:**<br /><br />Exit-Handler-werden zugeordnet.<br /><br />Rückgängig-Handler-werden zugeordnet.<br /><br />Continue-Handler-werden nicht zugeordnet.<br /><br />Bedingungen: Es wird nicht der SQL Server-Semantik zugeordnet.|  
|Dynamische SQL-Anweisungen|Nicht zugeordnet.|  
|Aliase|Sind zugeordnet.|  
|Spitznamen|Partielle Zuordnung. Für das zugrunde liegende Objekt ist eine manuelle Verarbeitung erforderlich.|  
|Synonyme|Sind zugeordnet.|  
|Standard Funktionen in DB2|SSMA ordnet DB2-Standardfunktionen zu, wenn eine äquivalente Funktion in SQL Server verfügbar ist:|  
|Authorization|Nicht zugeordnet.|  
|Prädikate|Sind zugeordnet.|  
|SELECT INTO-Anweisung|Nicht zugeordnet.|  
|VALUES into-Anweisung|Nicht zugeordnet.|  
|Transaktions Steuerung|Nicht zugeordnet.|  
  
## <a name="converting-db2-database-objects"></a>Umstellen von DB2-Datenbankobjekten  
Zum Konvertieren von DB2-Datenbankobjekten wählen Sie zunächst die Objekte aus, die Sie konvertieren möchten, und lassen Sie dann die Konvertierung von SSMA durchführen. Wenn Sie während der Konvertierung Ausgabemeldungen anzeigen möchten, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So konvertieren Sie DB2-Objekte in SQL Server Syntax**  
  
1.  Erweitern Sie im DB2-metadatenexplorer den DB2-Server, und erweitern Sie dann **Schemas**.  
  
2.  Zu konvertierende Objekte auswählen:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Schemas**, um alle Schemas zu konvertieren.  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Schema Namen, um eine Datenbank zu konvertieren oder auszulassen.  
  
    -   Wenn Sie eine Kategorie von Objekten konvertieren oder weglassen möchten, erweitern Sie ein Schema, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Wenn Sie einzelne Objekte konvertieren oder weglassen möchten, erweitern Sie den Ordner Category, und aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, klicken Sie mit der rechten Maustaste auf **Schemas** , und wählen Sie **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten konvertieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann **Schema konvertieren**auswählen.  
  
## <a name="viewing-conversion-problems"></a>Anzeigen von Konvertierungs Problemen  
Einige DB2-Objekte werden möglicherweise nicht konvertiert. Sie können die Erfolgsraten der Konvertierung ermitteln, indem Sie den Zusammenfassungs Bericht für die Zusammenfassung anzeigen  
  
**So zeigen Sie einen Zusammenfassungs Bericht an**  
  
1.  Wählen Sie im DB2-metadatenexplorer **Schemas**aus.  
  
2.  Wählen Sie im rechten Bereich die Registerkarte **Bericht** aus.  
  
    Dieser Bericht zeigt den Zusammenfassungs Bewertungsbericht für alle Datenbankobjekte an, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungs Bericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie das Schema im DB2-metadatenexplorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt im DB2-metadatenexplorer aus. Bei Objekten, die Konvertierungsprobleme aufweisen, wird ein rotes Fehler Symbol angezeigt.  
  
Bei Objekten, die nicht erfolgreich konvertiert werden konnten, können Sie die Syntax anzeigen, die zu einem Konvertierungs Fehler geführt hat.  
  
**So zeigen Sie einzelne Konvertierungsprobleme an**  
  
1.  Erweitern Sie im DB2-metadatenexplorer **Schemas**.  
  
2.  Erweitern Sie das Schema, das ein rotes Fehler Symbol anzeigt.  
  
3.  Erweitern Sie unter dem Schema einen Ordner mit einem roten Fehler Symbol.  
  
4.  Wählen Sie das Objekt mit einem roten Fehler Symbol aus.  
  
5.  Klicken Sie im rechten Bereich auf die Registerkarte **Bericht** .  
  
6.  Am oberen Rand der Registerkarte **Bericht** befindet sich eine Dropdown Liste. Wenn in der Liste **Statistiken**angezeigt werden, ändern Sie die Auswahl in **Quelle**.  
  
    SSMA zeigt den Quellcode und mehrere Schaltflächen direkt oberhalb des Codes an.  
  
7.  Klicken Sie auf die Schaltfläche **nächstes Problem** . Dabei handelt es sich um ein rotes Fehler Symbol mit einem Pfeil, der nach rechts zeigt.  
  
    SSMA hebt den ersten problematischen Quell Code hervor, der im aktuellen-Objekt gefunden wird.  
  
Sie müssen für jedes Element, das nicht konvertiert werden konnte, bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für Prozeduren auf der Registerkarte " **SQL** " ändern.  
  
-   Sie können das Objekt in der DB2-Datenbank ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. Deaktivieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im metadatenexplorer und im DB2-metadatenexplorer das Kontrollkästchen neben dem Element, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie die Objekte in laden und Daten aus DB2 migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, [die konvertierten Objekte in SQL Server zu laden](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten in SQL Server &#40;DB2ToSQL-&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
