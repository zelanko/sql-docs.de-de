---
description: Projekteinstellungen (Konvertierung) (MySqlToSql)
title: Projekteinstellungen (Konvertierung) (mysqltoisql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 4c2c4c093fec21723584538dfb5585a74e15c8fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492433"
---
# <a name="project-settings-conversion-mysqltosql"></a>Projekteinstellungen (Konvertierung) (MySqlToSql)
Die Seite Konvertierung des Dialog Felds **Projekteinstellungen** enthält Einstellungen, mit denen Sie anpassen können, wie SSMA die MySQL-Syntax in SQL Server oder SQL Azure Syntax konvertiert.  
  
Der Bereich Konvertierung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld **Standard Projekteinstellungen** , um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die Konvertierungs Einstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp, für den die Einstellungen angezeigt werden müssen/Changed in der Dropdown Liste **Migrations Ziel Version** aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, klicken Sie **im Menü Extras** auf **Projekteinstellungen**, klicken Sie dann unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.  
  
## <a name="options"></a>Tastatur  
  
### <a name="collate-clause"></a>COLLATE-Klausel  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Explizite Konvertierung der COLLATE-Klausel**|Die explizite Konvertierung der COLLATE-Klausel gibt an, wie explizite COLLATE-Klauseln in MySQL-Code konvertiert werden. Mögliche Optionen: ignorieren und mit einer Warnung versehen/Fehler generieren<br /><br />**Standardmodus**: ignorieren und mit einer Warnung markieren<br /><br />**Optimistischer Modus**: ignorieren und mit einer Warnung markieren<br /><br />**Vollständiger Modus**: ignorieren und mit einer Warnung markieren|  
  
### <a name="column-constraints"></a>Spalten Einschränkungen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Einschränkung für Spalten des enum-Datentyps generieren**|Generiert eine Einschränkung für Spalten des enum-Datentyps in der SQL Server oder SQL Azure Tabelle, wenn Sie nicht in der MySQL-Tabelle vorhanden ist. Wenn ja, werden alle konvertierten Spalten des enumerationsdatentyps mit der Check-Einschränkung begleitet, die den Wert steuert.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Einschränkung für Spalten des Set-Datentyps generieren**|Generiert eine Einschränkung für Spalten des Set-Datentyps in der SQL Server oder SQL Azure Tabelle, wenn Sie nicht in der MySQL-Tabelle vorhanden ist. Wenn ja, werden alle konvertierten Spalten des Set-Datentyps mit der Check-Einschränkung begleitet, die den Wert steuert.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Generieren einer Einschränkung für Spalten mit nicht signierten numerischen Datentyp Spalten**|Fügen Sie Spalten mit nicht signierten numerischen Datentypen eine Überprüfung auf einen nicht negativen Wert hinzu.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Einschränkung für "Year"-Datentyp Spalten generieren**|Generiert eine Einschränkung für die Spalten des Datentyps Year in der SQL Server oder SQL Azure Tabelle, wenn Sie nicht in der MySQL-Tabelle vorhanden ist. Wenn ja, werden alle konvertierten Spalten des Year-Datentyps mit der Check-Einschränkung begleitet, die den Wert steuert.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
  
### <a name="data-types"></a>Datentypen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Datentyp Konvertierung in Enum**|Gibt an, wie der MySQL-Aufzählungs Datentyp entweder als in nvarchar konvertieren oder in numeric konvertieren konvertiert werden soll.<br /><br />**Standardmodus**: in nvarchar konvertieren<br /><br />**Optimistischer Modus**: in nvarchar konvertieren<br /><br />**Vollständiger Modus**: in nvarchar konvertieren|  
|**Datentyp Konvertierung festlegen**|Gibt an, wie der MySQL-Set-Datentyp konvertiert werden soll, konvertiert in nvarchar (l)/Convert in binary (l).<br /><br />**Standardmodus**: in nvarchar (L) konvertieren<br /><br />**Optimistischer Modus**: in nvarchar (L) konvertieren<br /><br />**Vollständiger Modus**: in nvarchar (L) konvertieren|  
  
### <a name="generic"></a>Allgemein  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Spalten ohne Standardwert in INSERT und replace**|Wenn "yes" lautet, sollten alle Anweisungen, die auf Tabellen mit anderen gespeicherten Modulen als MyISAM und InnoDB verweisen, mit Warn Meldungs Meldungen gekennzeichnet werden.<br /><br />**Standardmodus**: zu Spaltenliste hinzufügen<br /><br />**Optimistischer Modus**: zu Spaltenliste hinzufügen<br /><br />**Vollmodus**: zu Spaltenliste hinzufügen|  
|**Division durch NULL-Konvertierung erzeugt**|Gibt an, ob MySQL ohne ERROR_FOR_DIVISION_BY_ZERO Verhalten emuliert werden soll.<br /><br />**Standardmodus**: Fehler<br /><br />**Optimistischer Modus**: Fehler<br /><br />**Vollständiger Modus**: NULL|  
|**IN-Operator**|Gibt an, wie MySQL in-Operator konvertiert wird.<br /><br />**Standardmodus**: immer konvertieren in in<br /><br />**Optimistischer Modus**: immer konvertieren in in<br /><br />**Vollständiger Modus**: bei Bedarf erweitern|  
|**MySQL-Funktions Konvertierung**|Gibt an, wie MySQL-Standardfunktionen konvertiert werden.<br /><br />**Standardmodus**: optimistisch<br /><br />**Optimistischer Modus**: optimistisch<br /><br />**Vollständiger Modus**: präzise|  
|**Nicht unterstützte Speicher-Engines**|Wenn "yes" lautet, sollten alle Anweisungen, die auf Tabellen mit anderen gespeicherten Modulen als MyISAM und InnoDB verweisen, mit Warn Meldungs Meldungen gekennzeichnet werden.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**ROWID-Erweiterungs Spalten Generierung unterdrücken**|Wenn ja, wird die Erstellung von rowd-Erweiterungs Spalten in Ziel Tabellen nicht untersagt. Kann sich auf die Migration einiger-Strukturen auswirken.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollmodus**: Nein|  
|**TRUNCATE-Anweisungs Konvertierung**|Gibt an, wie TRUNCATE-Anweisungen konvertiert werden.<br /><br />**Standardmodus**: Abschneiden<br /><br />**Optimistischer Modus**: Abschneiden<br /><br />**Vollständiger Modus**: Abschneiden|  
  
### <a name="misc"></a>Sonstiges  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Standard Schema Zuordnung**|Gibt an, wie MySQL-Datenbanken SQL Server Schemas zugeordnet werden.<br /><br />**Standardmodus**: Datenbank in Datenbank<br /><br />**Optimistischer Modus**: Datenbank in Datenbank<br /><br />**Vollständiger Modus**: Datenbank in Datenbank|  
  
### <a name="procedures-and-functions"></a>Prozeduren und Funktionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Standard Funktions Konvertierung**|Gibt an, ob Funktionen standardmäßig in T-SQL-Funktionen oder gespeicherte Prozeduren konvertiert werden sollen.<br /><br />**Standardmodus**: in Funktion konvertieren<br /><br />**Optimistischer Modus**: in Funktion konvertieren<br /><br />**Vollständiger Modus**: in Funktion konvertieren|  
|**SET-XACT_ABORT generieren**|Gibt an, ob festgelegt wird, XACT_ABORT on am Anfang der konvertierten Prozedur oder des Auslösers hinzugefügt werden muss.<br /><br />**Standardmodus**: Ja<br /><br />**Optimistischer Modus**: Ja<br /><br />**Vollständiger Modus**: Ja|  
|**SET NOCOUNT ON generieren**|Gibt an, ob SET NOCOUNT ON am Anfang der konvertierten Prozedur oder des Auslösers eingefügt werden muss.<br /><br />**Standardmodus**: Ja<br /><br />**Optimistischer Modus**: Ja<br /><br />**Vollständiger Modus**: Ja|  
  
### <a name="spatial-data-types"></a>Räumliche Datentypen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Standardmäßiges Begrenzungsfeld {xmax&#124;xmin&#124;ymax&#124;ymin} für räumliche Indizes**|Definiert den Standardwert für den Parameter "{xmax&#124;xmin&#124;ymax&#124;ymin}" des Begrenzungs Rahmens, der in räumlichen Indizes verwendet wird.<br /><br />**Standardmodus**<br /><br />Xmax: 100<br /><br />Xmin: 0<br /><br />Ymax: 100<br /><br />Ymin: 0<br /><br />**Optimistischer Modus**<br /><br />Xmax: 100<br /><br />Xmin: 0<br /><br />Ymax: 100<br /><br />Ymin: 0<br /><br />**Vollständiger Modus**<br /><br />Xmax: 100<br /><br />Xmin: 0<br /><br />Ymax: 100<br /><br />Ymin: 0|  
|**Standardmäßige Raster Dichte für räumliche Indizes**|Definiert den Standardwert für LEVEL_1, LEVEL_2, LEVEL_3 und LEVEL_4 der in räumlichen Indizes verwendeten Raster Dichte.<br /><br />**Standardmodus**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard<br /><br />**Optimistischer Modus**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard<br /><br />**Vollständiger Modus**<br /><br />LEVEL_1: Standard<br /><br />LEVEL_2: Standard<br /><br />LEVEL_3: Standard<br /><br />LEVEL_4: Standard|  
  
### <a name="transactions"></a>Transaktionen  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Nicht transaktionale Tabellen**|Gibt an, ob alle Verweise auf die Tabelle, die keine Transaktionen unterstützen, mit Warn Meldungs Meldungen markiert werden sollen.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Transaktions Isolationsstufe**|Gibt an, welche Transaktions Isolationsstufe für neue Transaktionen verwendet werden soll.<br /><br />**Standardmodus**: Standard<br /><br />**Optimistischer Modus**: Standard<br /><br />**Vollständiger Modus**: wiederholbarer Lesevorgang|  
  
### <a name="value-control"></a>Wertsteuer Element  
  
|||  
|-|-|  
|**Begriff**|**Definition**|  
|**Konvertieren von Zeichen in numerische Zeichen**|Gibt an, wie die implizite und explizite Konvertierung des Zeichen Datentyps in numerische Datentypen behandelt werden soll.<br /><br />**Standardmodus**: optimistisch<br /><br />**Optimistischer Modus**: optimistisch<br /><br />**Vollständiger Modus**: präzise|  
|**Steuern von numerischen Werten ohne Vorzeichen**|Steuern Sie das Zuweisen von Werten zu numerischen Variablen und Parametern ohne Vorzeichen.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollständiger Modus**: Ja|  
|**Nicht signierte Subtraktion Steuern**|Ändern Sie negative Werte, die in Tabellen Spalten des Datentyps ohne Vorzeichen eingefügt werden.<br /><br />**Standardmodus**: "as-is" konvertieren<br /><br />**Optimistischer Modus**: "as-is" konvertieren<br /><br />**Vollmodus**: Markierung mit einer Warnung|  
|**Konvertierung in und aus binary-Datentyp**|Gibt an, wie die implizite und explizite Konvertierung des binären Datentyps behandelt werden soll.<br /><br />**Standardmodus**: optimistisch<br /><br />**Optimistischer Modus**: optimistisch<br /><br />**Vollständiger Modus**: präzise|  
|**Konvertierung in Datums-/Uhrzeit-Datentyp**|Gibt an, wie die implizite und explizite Konvertierung in den Datums-/Uhrzeitdatentyp behandelt werden soll.<br /><br />**Standardmodus**: Emulieren des MySQL-Formats<br /><br />**Optimistischer Modus**: Verwenden des SQL Server Formats<br /><br />**Vollständiger Modus**: Emulieren des MySQL-Formats|  
|**Numerische Literale mit einer Genauigkeit von mehr als 38**|Gibt an, wie numerische Literale mit einer Genauigkeit konvertiert werden, die 38 überschreitet.<br /><br />**Standardmodus**: Runden, wenn möglich<br /><br />**Optimistischer Modus**: Runden, wenn möglich<br /><br />**Vollständiger Modus**: Round, wenn möglich|  
|**NULL-Date in NOT NULL-Spalten**|Gibt an, wie die Zuweisung zu NOT NULL-Spalten mit NULL-Date-, Zero-in-Date-oder ungültigen Datums-/Uhrzeitwerten behandelt werden soll.<br /><br />**Standardmodus**: GETDATE ()<br /><br />**Optimistischer Modus**: GETDATE ()<br /><br />**Vollständiger Modus**: GETDATE ()|  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;mysqltosql&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
