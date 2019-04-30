---
title: Projekteinstellungen (Konvertierung) (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 12e2e61c6b55bf3c549c08f2b090059d674ed83d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63162027"
---
# <a name="project-settings-conversion-mysqltosql"></a>Projekteinstellungen (Konvertierung) (MySqlToSql)
Die Seite die **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA MySQL-Syntax in SQL Server oder SQL Azure-Syntax konvertiert.  
  
Im Bereich für die Konvertierung finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Verwenden der **Projekt Standardeinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für alle Projekte. Die Konvertierungseinstellungen für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden,  **Migration Zielversion** Dropdown-Liste, klicken Sie auf **allgemeine** am unteren Rand der linken Seite, und wählen Sie dann **Konvertierung**.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** klicken Sie im Menü **Projekteinstellungen**, klicken Sie dann auf **allgemeine** am unteren Rand im linken Bereich, und klicken Sie dann auf **Konvertierung**.  
  
## <a name="options"></a>Optionen  
  
### <a name="collate-clause"></a>COLLATE-Klausel  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Explizite Konvertierung der COLLATE-Klausel**|Explizite Konvertierungsoption für COLLATE-Klausel gibt an, wie explizite COLLATE-Klauseln im MySQL-Code zu konvertieren. Mögliche Optionen: Ignorieren und mit einer Warnung markieren / generiert einen Fehler<br /><br />**Im Modus Standard**:  Ignorieren und mit einer Warnung<br /><br />**Vollständige**:  Ignorieren und mit einer Warnung<br /><br />**Vollständiger Modus**:  Ignorieren und mit einer Warnung|  
  
### <a name="column-constraints"></a>Spalteneinschränkungen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Einschränkung für Spalten des Datentyps für die Enumeration generieren**|Für Spalten des Datentyps für die Enumeration-Einschränkung in der SQL Server oder SQL Azure-Tabelle generiert, wenn es nicht in der MySQL-Tabelle vorhanden ist. Falls Ja, werden alle konvertierte Spalten des Datentyps für die Enumeration mit CHECK-Einschränkung, die steuern Sie den Wert des begleitet werden.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
|**Einschränkung für Spalten vom Datentyp festlegen zu generieren.**|Einschränkung für Spalten des Datentyps für die Gruppe in der SQL Server oder SQL Azure-Tabelle generiert, wenn es nicht in der MySQL-Tabelle vorhanden ist. Falls Ja, werden alle konvertierte Spalten des Datentyps für die Gruppe mit CHECK-Einschränkung, die steuern Sie den Wert des begleitet werden.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
|**Generieren Sie Einschränkung für Spalten mit Spalten vom Typ ohne Vorzeichen numerische Daten**|Fügen Sie Überprüfung für den nicht negativen Wert hinzu, Spalten ohne Vorzeichen numerischen Datentypen.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
|**Einschränkung für Jahresspalten generieren**|Einschränkung für Jahr-datentypspalten in der SQL Server oder SQL Azure-Tabelle generiert, wenn es nicht in der MySQL-Tabelle vorhanden ist. Falls Ja, konvertiert alle Spalten der Daten für das Jahr Typ mit CHECK-Einschränkung, die steuern Sie den Wert des begleitet.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
  
### <a name="data-types"></a>Datentypen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**ENUM-datentypkonvertierungen**|Gibt an, wie MySQL ENUM-Datentyp konvertiert werden soll, entweder als in NVARCHAR konvertieren oder Umwandeln in "Numerisch"<br /><br />**Im Modus Standard**:  In NVARCHAR konvertieren<br /><br />**Vollständige**:  In NVARCHAR konvertieren<br /><br />**Vollständiger Modus**:  In NVARCHAR konvertieren|  
|**SET-datentypkonvertierungen**|Gibt an, wie Festlegen von MySQL-Datentyp sollte zu konvertieren, NVARCHAR (L) konvertiert, und Konvertieren in BINARY(L)<br /><br />**Im Modus Standard**: Konvertieren in NVARCHAR(L)<br /><br />**Vollständige**: Konvertieren in NVARCHAR(L)<br /><br />**Vollständiger Modus**: Konvertieren in NVARCHAR(L)|  
  
### <a name="generic"></a>Generisch  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Spalten ohne Standardwert in INSERT- und ersetzen**|Wenn 'Ja', sollte alle Anweisungen, die mithilfe von gespeicherten Engines als MyISAM-Tabellen und InnoDb Tabellen verweisen, die mit Warnmeldungen für die Konvertierung markiert werden.<br /><br />**Im Modus Standard**:  Liste der Spalten hinzufügen<br /><br />**Vollständige**:  Liste der Spalten hinzufügen<br /><br />**Vollständiger Modus**:   Liste der Spalten hinzufügen|  
|**Division durch 0 (null) Konvertierung erzeugt.**|Gibt an, ob MySQL ohne ERROR_FOR_DIVISION_BY_ZERO Verhalten zu emulieren.<br /><br />**Im Modus Standard**:   Fehler<br /><br />**Vollständige**:  Fehler<br /><br />**Vollständiger Modus**:   NULL|  
|**IN-Operator**|Gibt an, wie IN der MySQL-Operator zu konvertieren.<br /><br />**Im Modus Standard**:   Immer in IN konvertieren<br /><br />**Vollständige**:  Immer in IN konvertieren<br /><br />**Vollständiger Modus**:   Erweitern Sie bei Bedarf|  
|**Konvertierung von MySQL-Funktion**|Gibt an, wie MySQL-Standardfunktionen zu konvertieren.<br /><br />**Im Modus Standard**:   Optimistisch<br /><br />**Vollständige**:  Optimistisch<br /><br />**Vollständiger Modus**:   Precise|  
|**Speicher-Engines unterstützt nicht**|Wenn 'Ja', sollte alle Anweisungen, die mithilfe von gespeicherten Engines als MyISAM-Tabellen und InnoDb Tabellen verweisen, die mit Warnmeldungen für die Konvertierung markiert werden.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
|**Unterdrücken der ROWID zusätzlichen Spalte generieren**|Falls Ja, verhindert die Erstellung von ROWD zusätzlichen Spalte erstellen, auf die Zieltabellen. Kann sich auf die Migration einige Strukturen auswirken.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Nein|  
|**TRUNCATE-anweisungskonvertierung**|Gibt an, wie kürzungsanweisungen zu konvertieren.<br /><br />**Im Modus Standard**:   TRUNCATE<br /><br />**Vollständige**:  TRUNCATE<br /><br />**Vollständiger Modus**:   TRUNCATE|  
  
### <a name="misc"></a>Sonstiges  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Standardmäßige Schemazuordnung**|Gibt an, wie Sie MySQL-Datenbanken in SQL Server-Schemas zuordnen.<br /><br />**Im Modus Standard**:  Datenbank zu einer Datenbank<br /><br />**Vollständige**:  Datenbank zu einer Datenbank<br /><br />**Vollständiger Modus**:  Datenbank zu einer Datenbank|  
  
### <a name="procedures-and-functions"></a>Prozeduren und Funktionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Standardkonvertierung-Funktion**|Gibt an, ob es sich bei Funktionen konvertiert werden sollen in der Standardeinstellung werden T-SQL-Funktionen oder gespeicherte Prozeduren.<br /><br />**Im Modus Standard**:  Konvertieren in Funktion<br /><br />**Vollständige**:  Konvertieren in Funktion<br /><br />**Vollständiger Modus**:  Konvertieren in Funktion|  
|**Generate SET XACT_ABORT ON**|Gibt an, ob SET XACT_ABORT ON an den Anfang der konvertierten Prozedur oder des Triggers hinzugefügt werden muss.<br /><br />**Im Modus Standard**:  Ja<br /><br />**Vollständige**:  Ja<br /><br />**Vollständiger Modus**:  Ja|  
|**Generieren von SET NOCOUNT auf**|Gibt an, ob SET NOCOUNT ON an den Anfang der konvertierten Prozedur oder des Triggers hinzugefügt werden muss.<br /><br />**Im Modus Standard**:  Ja<br /><br />**Vollständige**:  Ja<br /><br />**Vollständiger Modus**:  Ja|  
  
### <a name="spatial-data-types"></a>Räumliche Datentypen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Umgebendes Feld standardmäßig {"xmax"&#124;"xmin"&#124;YMAX&#124;YMIN} für räumliche Indizes**|Definiert die Standard-Wert für {"xmax"&#124;"xmin"&#124;YMAX&#124;YMIN}-Parameter des umgebenden Felds in räumlichen Indizes verwendet.<br /><br />**Standardmodus**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0<br /><br />**Vollständige**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX:  100<br /><br />YMIN: 0<br /><br />**Vollständigen-Modus**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0|  
|**Standardmäßig die Dichte des Rasters für räumliche Indizes**|Definiert Standardwert für LEVEL_1, LEVEL_2, LEVEL_3 und LEVEL_4, der die Dichte des Rasters in räumlichen Indizes verwendet.<br /><br />**Standardmodus**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard<br /><br />**Vollständige**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard<br /><br />**Vollständigen-Modus**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard|  
  
### <a name="transactions"></a>Transaktionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Nicht-transaktionale Tabellen**|Gibt an, und zwar unabhängig davon, ob alle Verweise auf die Tabelle, die keine Transaktionen unterstützen, die mit Warnmeldungen für die Konvertierung gekennzeichnet werden soll.<br /><br />**Im Modus Standard**: Nein<br /><br />**Vollständige**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Transaktionsisolationsstufe**|Gibt an, welche Isolationsstufe für Transaktionen für neue Transaktionen verwendet werden soll.<br /><br />**Im Modus Standard**:   Standard<br /><br />**Vollständige**:  Standard<br /><br />**Vollständiger Modus**:   Repeatable Read|  
  
### <a name="value-control"></a>Steuerelement für Werte  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Zeichen, das numerische Konvertierung**|Gibt das implizite und explizite Konvertierung von Character-Datentyp in numerische Datentypen zu behandeln.<br /><br />**Im Modus Standard**:   Optimistisch<br /><br />**Vollständige**:  Optimistisch<br /><br />**Vollständiger Modus**:   Precise|  
|**Steuern von numerischen Werten ohne Vorzeichen**|Zuweisen von Werten ohne Vorzeichen numerischen Variablen und Parameter-Steuerelement.<br /><br />**Im Modus Standard**:   Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:   Ja|  
|**Steuern von nicht SIGNIERTEN Subtraktion**|Ändern Sie negative Werte in Spalten der Tabelle ohne Vorzeichen Datentyp eingefügt.<br /><br />**Im Modus Standard**:   Konvertieren von "als-ist"<br /><br />**Vollständige**:  Konvertieren von "als-ist"<br /><br />**Vollständiger Modus**:   Markieren Sie eine Warnung|  
|**Konvertierung in und aus dem Binary-Datentyp**|Gibt das implizite und explizite Konvertierung von Binary-Datentyp behandeln.<br /><br />**Im Modus Standard**:   Optimistisch<br /><br />**Vollständige**:  Optimistisch<br /><br />**Vollständiger Modus**:   Precise|  
|**Geben Sie die Konvertierung in Datum/Uhrzeit-Daten**|Gibt wie, behandeln implizite und explizite Konvertierung in ein Datum/Uhrzeit-Datentyp.<br /><br />**Im Modus Standard**:   Emulieren Sie MySQL-format<br /><br />**Vollständige**:  Verwenden Sie SQL Server-format<br /><br />**Vollständiger Modus**:   Emulieren Sie MySQL-format|  
|**Numerische Literale mit einer Genauigkeit von 38 überschreitet**|Gibt an, wie numerische Literale mit einer Genauigkeit von 38 überschreitet zu konvertieren.<br /><br />**Im Modus Standard**:   Runden Sie wenn möglich<br /><br />**Vollständige**:  Runden Sie wenn möglich<br /><br />**Vollständiger Modus**:   Runden Sie wenn möglich|  
|**NULL-Datum in NOT NULL-Spalten**|Gibt das Durchführen von Zuweisung zu NOT NULL-Spalten von 0 (null) bis Datum, 0 (null)-im-Date oder ungültige Datum/Uhrzeit-Werte.<br /><br />**Im Modus Standard**:   GETDATE()<br /><br />**Vollständige**:  GETDATE()<br /><br />**Vollständiger Modus**:   GETDATE()|  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
