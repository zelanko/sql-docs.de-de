---
title: Konvertieren von DB2-Schemas (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7947efc3-ca86-4ec5-87ce-7603059c75a0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d509ad58491bca379e3ab86e07aee63e8a5d3946
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298967"
---
# <a name="converting-db2-schemas-db2tosql"></a>Konvertieren von DB2-Schemas (DB2ToSQL)
Nachdem Sie eine Verbindung mit DB2 hergestellt haben, verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und das Projekt festlegen und Optionen für die Zuordnung von Daten, können Sie die DB2-Datenbankobjekte zu konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekten.  
  
## <a name="the-conversion-process"></a>Konvertierungsprozess  
Die Objektdefinitionen aus DB2 akzeptiert, konvertiert diese in ähnliche konvertieren Datenbankobjekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte und lädt dann diese Informationen in der SSMA-Metadaten. Er lädt nicht die Informationen in die Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können dann die Objekte und deren Eigenschaften anzeigen, mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer.  
  
Bei der Konvertierung gibt SSMA Ausgabe in den Bereich Ausgabe und Fehlermeldungen in den Bereich Fehlerliste angezeigt. Verwenden Sie die Ausgabe- und Informationen, um festzustellen, ob Sie so ändern Sie die DB2-Datenbanken oder den Konvertierungsprozess Ihrer, um die gewünschte Konvertierungsergebnisse erhalten haben.  
  
## <a name="setting-conversion-options"></a>Festlegen von Optionen  
Lesen Sie vor dem Konvertieren von Objekten, die die Projektoptionen für die Konvertierung in den **Projekteinstellungen** Dialogfeld. Verwenden Sie das Dialogfeld zu öffnen, können Sie festlegen, wie der SSMA-Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
## <a name="conversion-results"></a>Konvertierungsergebnisse  
Die folgende Tabelle zeigt, welche DB2 Objekte konvertiert werden, und das resultierende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte:  
  
|DB2-Objekte|Resultierende SQL Server-Objekte|  
|-----------|----------------------------|  
|Datentypen|**SSMA wird jeder Typ, mit Ausnahme der unten aufgeführten Folgendes:**<br /><br />CLOB: Einige systemeigenen Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. B. CLOB_EMPTY())<br /><br />BLOB: Einige systemeigenen Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. B. BLOB_EMPTY())<br /><br />DBLOB: Einige systemeigenen Funktionen für die Arbeit mit diesem Typ werden nicht unterstützt (z. B. DBLOB_EMPTY())|  
|Benutzerdefinierte Typen|**SSMA ordnet die folgenden benutzerdefinierten:**<br /><br />Gesonderter Typ<br /><br />Strukturierten Typ<br /><br />SQL-PL-Datentypen – Hinweis: Schwache Cursortyp werden nicht unterstützt.|  
|Spezielle Register|**SSMA wird nur registriert, die unten aufgeführten:**<br /><br />AKTUELLER ZEITSTEMPEL<br /><br />AKTUELLES DATUM<br /><br />AKTUELLE ZEIT<br /><br />AKTUELLE ZEITZONE<br /><br />AKTUELLER BENUTZER<br /><br />SESSION_USER und Benutzer<br /><br />SYSTEM_USER<br /><br />CURRENT CLIENT_APPLNAME<br /><br />CURRENT CLIENT_WRKSTNNAME<br /><br />AKTUELLE SPERRUNGSTIMEOUT<br /><br />AKTUELLES SCHEMA<br /><br />AKTUELLER SERVER<br /><br />AKTUELLE ISOLATION<br /><br />Andere spezielle registriert werden nicht auf SQLServer semantic zugeordnet.|  
|CREATE TABLE|**SSMA wird CREATE TABLE, mit den folgenden Ausnahmen:**<br /><br />Mehrdimensionale clustering (MDC) Tabellen<br /><br />Bereich gruppierte Tabellen (RCT)<br /><br />Partitionierte Tabellen<br /><br />Getrennte Tabelle<br /><br />DATA CAPTURE-Klausel<br /><br />Option IMPLICITLY AUSGEBLENDET<br /><br />VOLATILE-option|  
|CREATE VIEW|SSMA ordnet CREATE VIEW mit "Mit lokalen CHECK OPTION" jedoch andere Optionen sind nicht auf SQL Server-Semantik zugeordnet|  
|CREATE INDEX|**SSMA wird die CREATE INDEX mit den folgenden Ausnahmen:**<br /><br />XML-Index<br /><br />Option BUSINESS_TIME ohne ÜBERSCHNEIDUNGEN<br /><br />PARTITIONIERTE-Klausel<br /><br />Spezifikation nur die option<br /><br />Mithilfe der erweitern-option<br /><br />MINPCTUSED-option<br /><br />SEITENTEILUNG-option|  
|Trigger|**SSMA wird der folgende Triggersemantik:**<br /><br />Nach dem / EACH ROW-Trigger<br /><br />Nach dem /FOR löst jeder Anweisung<br /><br />VOR / EACH Zeile und anstelle von / EACH ROW-Trigger|  
|Sequenzen|Zugeordnet sind.|  
|SELECT-Anweisung|**Wählen Sie SSMA-Zuordnungen mit den folgenden Ausnahmen:**<br /><br />Daten-Change-Tabelle-Reference-Klausel – teilweise zugeordnet, aber die endgültigen Tabellen wird nicht unterstützt<br /><br />Tabelle-Reference-Klausel – teilweise zugeordnet, aber nur-Tabelle-Reference, outer Table-Verweis, Analyze_table-Ausdruck, Auflistung abgeleitete Tabelle, Xmltable-Ausdruck nicht SQL Server-Semantik zugeordnet sind<br /><br />Punkt-zu-Spezifikation-Klausel - nicht zugeordnet.<br /><br />Weiterhin-Handler-Klausel - nicht zugeordnet.<br /><br />Typisierte-Abhängigkeitsklausel - nicht zugeordnet.<br /><br />Gleichzeitiger Zugriff-Auflösung-Klausel - nicht zugeordnet.|  
|VALUES-Anweisung|Zugeordnet ist.|  
|INSERT-Anweisung|Zugeordnet ist.|  
|UPDATE-Anweisung|S**SMA ordnet UPDATE mit den folgenden Ausnahmen:**<br /><br />Tabellenverweis Klausel - nur-Tabelle-Verweis ist nicht auf SQL Server-Semantik zugeordnet.<br /><br />Punkt-Klausel – ist nicht zugeordnet.|  
|MERGE-Anweisung|**SSMA ordnet MERGE mit den folgenden Ausnahmen:**<br /><br />Einzelne und mehrere Vorkommen of Each-Klausel: SQL Server-Semantik für die einzelnen Klauseln beschränkt Vorkommen zugeordnet ist<br /><br />SIGNAL-Klausel – entspricht keinem SQL Server-Semantik<br /><br />Gemischte Update- und DELETE-Klauseln - Semantik von SQL Server nicht zugeordnet<br /><br />Punkt-Klausel - entspricht keinem SQL Server-Semantik|  
|DELETE-Anweisung|**SSMA-Zuordnungen löschen mit den folgenden Ausnahmen:**<br /><br />Tabellenverweis Klausel - nur-Tabelle-Verweis ist nicht auf SQL Server-Semantik zugeordnet.<br /><br />Punkt-Klausel – entspricht keinem SQL Server-Semantik|  
|Isolationsstufe und Sperrentyp|Zugeordnet ist.|  
|Prozeduren (SQL)|Zugeordnet sind.|  
|Prozeduren (extern)|Manuelles Update erforderlich.|  
|Prozeduren (Quelle)|SQL Server-Semantik nicht zugeordnet.|  
|Zuweisungsanweisung|Zugeordnet ist.|  
|CALL-Anweisung für eine Prozedur|Zugeordnet ist.|  
|CASE-Anweisung|Zugeordnet ist.|  
|FÜR die Anweisung|Zugeordnet ist.|  
|GOTO-Anweisung|Zugeordnet ist.|  
|IF-Anweisung|Zugeordnet ist.|  
|Durchlaufen Sie die Anweisung|Zugeordnet ist.|  
|Lassen SIE die Anweisung|Zugeordnet ist.|  
|LOOP-Anweisung|Zugeordnet ist.|  
|Wiederholen SIE die Anweisung|Zugeordnet ist.|  
|Zeigen Sie die Anweisung|Bedingungen werden nicht unterstützt. Nachrichten können optional sein.|  
|RETURN-Anweisung|Zugeordnet ist.|  
|SIGNAL-Anweisung|Bedingungen werden nicht unterstützt. Nachrichten können optional sein.|  
|WHILE-Anweisung|Zugeordnet ist.|  
|GET-Diagnose-Anweisung|**SSMA ordnet Diagnose zu erhalten, mit den folgenden Ausnahmen:**<br /><br />Die ROW_COUNT - zugeordnet ist.<br /><br />DB2_RETURN_STATUS – zugeordnet ist.<br /><br />MESSAGE_TEXT – zugeordnet ist.<br /><br />DB2_SQL_NESTING_LEVEL - entspricht keinem SQL Server-Semantik<br /><br />DB2_TOKEN_STRING - entspricht keinem SQL Server-Semantik|  
|Cursor|**SSMA ordnet Cursor mit den folgenden Ausnahmen:**<br /><br />ALLOCATE-CURSOR-Anweisung – entspricht keinem SQL Server-Semantik<br /><br />Zuordnen von LOCATORS Statement - entspricht keinem SQL Server-Semantik<br /><br />DECLARE CURSOR-Anweisung - Returnability-Klausel ist nicht auf SQL Server-Semantik zugeordnet.<br /><br />FETCH-Anweisung - partielle datenzuordnung. Variablen, die als Ziel werden nur unterstützt. SQLDA-Deskriptor ist nicht auf SQL Server-Semantik zugeordnet.|  
|Variablen|Zugeordnet sind.|  
|Ausnahmen, Handler und Bedingungen|**SSMA wird "Behandlung von Ausnahmen" mit den folgenden Ausnahmen:**<br /><br />Handler zu beenden: zugeordnet sind.<br /><br />Handler rückgängig zu machen – zugeordnet sind.<br /><br />Handler - fortsetzen, werden nicht zugeordnet.<br /><br />Bedingungen - ist es nicht SQL Server-Semantik zugeordnet.|  
|Dynamische SQL-Anweisungen|Nicht zugeordnet.|  
|Aliase|Zugeordnet sind.|  
|Spitznamen|Partielle datenzuordnung. Manuelle Verarbeitung ist für die zugrunde liegende Objekt erforderlich|  
|Synonyme|Zugeordnet sind.|  
|Standardfunktionen in DB2|SSMA wird DB2-Standardfunktionen, wenn eine gleichwertige Funktion in SQL Server verfügbar ist:|  
|Autorisierung|Nicht zugeordnet.|  
|Prädikate|Zugeordnet sind.|  
|SELECT INTO-Anweisung|Nicht zugeordnet.|  
|Werte INTO-Anweisung|Nicht zugeordnet.|  
|Transaktionssteuerung|Nicht zugeordnet.|  
  
## <a name="converting-db2-database-objects"></a>Konvertieren von DB2-Datenbankobjekte  
Um DB2-Datenbankobjekte zu konvertieren, wählen Sie zuerst die Objekte, die Sie konvertieren möchten, und lassen Sie dann die SSMA, die die Konvertierung nicht ausgeführt. Anzeigen von ausgehenden Nachrichten bei der Konvertierung auf den **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**So konvertieren Sie DB2-Objekte in SQL Server-syntax**  
  
1.  In DB2-Metadaten-Explorer, erweitern Sie den DB2-Server, und klicken Sie dann **Schemas**.  
  
2.  Wählen Sie Objekte zu konvertieren:  
  
    -   Um alle Schemas zu konvertieren, wählen Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum konvertieren, oder lassen Sie eine Datenbank, wählen Sie das Kontrollkästchen neben dem Schemanamen.  
  
    -   Konvertieren, oder lassen Sie eine Kategorie von Objekten, erweitern Sie ein Schema, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Konvertieren, oder lassen Sie einzelne Objekte, erweitern Sie die Kategorieordner, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, Maustaste **Schemas** , und wählen Sie **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten von der rechten Maustaste auf das Objekt oder der übergeordnete Ordner, und wählen Sie dann konvertieren **Schema konvertieren**.  
  
## <a name="viewing-conversion-problems"></a>Probleme bei der Konvertierung anzeigen  
Einige Objekte für DB2 können nicht konvertiert werden. Sie können die Abschlussraten für den Erfolg bestimmen, durch Anzeigen der Zusammenfassung Konvertierungsbericht.  
  
**Zum Anzeigen eines Übersichtsberichts**  
  
1.  Wählen Sie in der DB2-Metadaten-Explorer, **Schemas**.  
  
2.  Wählen Sie im rechten Bereich die **Bericht** Registerkarte.  
  
    Dieser Bericht zeigt die Zusammenfassung Bewertungsbericht für alle Datenbankobjekte, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungsbericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie das Schema in DB2-Metadaten-Explorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt in der DB2-Metadaten-Explorer aus. Objekten, die Probleme bei der Konvertierung zu haben, ist ein rotes Fehlersymbol.  
  
Für Objekte, die Konvertierung fehlgeschlagen ist, können Sie die Syntax anzeigen, die die Konvertierungsfehler bewirkt, dass geführt haben.  
  
**Probleme beim Konvertieren der einzelnen anzeigen**  
  
1.  Erweitern Sie in der DB2-Metadaten-Explorer, **Schemas**.  
  
2.  Erweitern Sie das Schema, das ein rotes Fehlersymbol zeigt.  
  
3.  Erweitern Sie einen Ordner mit einem roten Fehlersymbol, unter dem Schema.  
  
4.  Wählen Sie das Objekt mit einem roten Fehlersymbol.  
  
5.  Klicken Sie im rechten Bereich auf die **Bericht** Registerkarte.  
  
6.  Am oberen Rand der **Bericht** Registerkarte wird eine Dropdown-Liste. Wenn die Liste zeigt **Statistiken**, ändern Sie die Auswahl auf **Quelle**.  
  
    SSMA wird der Quellcode und verschiedene Schaltflächen direkt über dem Code angezeigt.  
  
7.  Klicken Sie auf die **nächsten Problem** Schaltfläche. Dies ist ein rotes Fehlersymbol mit einem Pfeil nach rechts.  
  
    SSMA wird es sich um den ersten problematisch Quellcode hervorheben, die, den Sie in das aktuelle Objekt findet.  
  
Für jedes Element, das nicht konvertiert werden konnten, müssen Sie bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für die Prozeduren auf die **SQL** Registerkarte.  
  
-   Sie können ändern, dass das Objekt in der DB2-Datenbank zu entfernen oder die problematischen Code zu überarbeiten. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer und DB2-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten aus DB2.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Laden Sie die konvertierte Objekte in SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Daten in SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
