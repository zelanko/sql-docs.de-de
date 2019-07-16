---
title: Project Settings (Migration) (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2f3c989626f36c003937723869b5e17d1a405ea9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67908867"
---
# <a name="project-settings-migration-mysqltosql"></a>Projekteinstellungen (Migration) (MySqlToSql)
Der Seite für die Migration von der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA Daten aus MySQL zu SQL Server migriert.  
  
Der Bereich für die Migration finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Die Einstellungen für alle SSMA-Projekten auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen den Projekttyp in **Migration Zielversion** Dropdown-Liste der die sollen die Einstellungen zuzugreifen, klicken Sie auf **allgemeine** am unteren Rand der linken Bereich ein, und klicken Sie dann auf **Migration**.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand im linken Bereich, und klicken Sie dann auf **Migration**.  
  
## <a name="options"></a>Optionen  
  
### <a name="bulk-copy"></a>Massenkopieren  
  
|Begriff|Definition|  
|--------|--------------|  
|**Batchgröße**|Gibt den Batch Größe, die während der Migration von Daten verwendet.<br /><br />**Im Modus Standard**:  1000<br /><br />**Vollständige**:  1000<br /><br />**Vollständiger Modus**:  1000|  
|**Check-Einschränkungen**|Gibt an, ob SSMA Einschränkungen überprüft werden sollen, wenn sie Daten in SQL Server-Tabellen einfügt.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
|**Trigger auslösen**|Gibt an, ob SSMA einfügen Trigger ausgelöst werden soll, wenn sie Daten in SQL Server-Tabellen hinzufügt.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
|**Identität beibehalten**|Gibt an, ob SSMA MySQL-Identity-Werte beibehält, wenn Daten mit SQL Server hinzugefügt. Der Wert "false" bewirkt, dass Identitätswerte vom Ziel zugewiesen werden soll.<br /><br />**Im Modus Standard**:  True<br /><br />**Vollständige**:  True<br /><br />**Vollständiger Modus**:  True|  
|**NULL-Werte beibehalten**|Gibt an, ob SSMA behält null-Werte in den Quelldaten aus, wenn Daten in SQL Server – unabhängig von den Standardwerten hinzugefügt, die in SQL Server angegeben werden.<br /><br />**Im Modus Standard**:  True<br /><br />**Vollständige**:  True<br /><br />**Vollständiger Modus**:  True|  
|**Tabellensperre**|Gibt an, ob es sich bei SSMA Tabellen sperrt, wenn sie Daten in Tabellen während der Datenmigration hinzufügt. Ruft eine Massenaktualisierungssperre für die Dauer des Massenkopiervorgangs ab. Wenn der Wert "false" ist, wird eine Sperre auf Zeilenebene festgelegt.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
  
### <a name="data-modification"></a>Datenänderung  
  
|Begriff|Definition|  
|--------|--------------|  
|**Ungültige Datumsangaben-Migration**|Gibt an, wie zum Migrieren ungültige Datumsangaben mit z. B. ' 2007-04-23 "oder" 2000-06-31 10:00:00 "in DATE und DATETIME-Formaten.<br /><br />**Im Modus Standard**:  NULL festlegen<br /><br />**Vollständige**:  NULL festlegen<br /><br />**Vollständiger Modus**:  NULL festlegen|  
|**Negative Zeitwerte Migration**|Gibt an, wie zum Migrieren von negativer Werten wie "-30:11:00" in-Spalten.<br /><br />**Im Modus Standard**:  NULL festlegen<br /><br />**Vollständige**:  NULL festlegen<br /><br />**Vollständiger Modus**:  NULL festlegen|  
|**TIME-Werten mehr als 24 Stunden Migration**|Gibt an, wie zum Migrieren von TIME-Werten von maximal ' 23: 59:59 "in-Spalten.<br /><br />**Im Modus Standard**:  NULL festlegen<br /><br />**Vollständige**:  NULL festlegen<br /><br />**Vollständiger Modus**:  NULL festlegen|  
|**Schneiden Sie binäre Werte in der Spalte passt ab**|Falls Ja, SSMA schneidet binäre Werte von MySQL auf, die nicht in SQL-Tabellenspalten passen, und Sie werden entsprechende Fehlermeldung generiert. Wenn Nein, verursacht die Zeile einen Fehler<br /><br />**Im Modus Standard**:  Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:  Nein|  
|**Abschneiden von Zeichenwerten enthalten, die in der Spalte passt**|SSMA schneidet Zeichenwerten enthalten, die von MySQL, die nicht in SQL-Tabellenspalten passen und entsprechende Fehlermeldung generiert.<br /><br />**Im Modus Standard**:  Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:  Nein|  
|**Keine Migration von Daten**|Gibt an, wie zum Migrieren von 0 (null) Daten wie "0000-00-00" oder "0000-00-00-00:00:00" in DATE und DATETIME-Spalten.<br /><br />**Im Modus Standard**:  NULL festlegen<br /><br />**Vollständige**:  NULL festlegen<br /><br />**Vollständiger Modus**:  NULL festlegen|  
|**0 (null) bei der Migration von Daten**|Gibt an, wie zum Migrieren von Daten mit 0 (null) Elementen, z. B. "2009-01-00" oder "2000-00-00-11:00:00" in DATE und DATETIME-Spalten.<br /><br />**Im Modus Standard**:  NULL festlegen<br /><br />**Vollständige**:  NULL festlegen<br /><br />**Vollständiger Modus**:  NULL festlegen|  
  
### <a name="migration-engine"></a>Ein Migrationsmodul  
  
|Begriff|Definition|  
|--------|--------------|  
|**Ein Migrationsmodul**|Gibt an, während der Datenmigration, verwendet Datenbank-Engine. Client-Side-Datenmigration bezieht sich auf SSMA-Client zum Abrufen der Daten aus der Quelle und die masseneinfügung von Daten in SQL Server. Datenmigration für Server-Seite bezieht sich auf SSMA Data Migration-Engine (Bulk Copy Program) auf das SQL Server als SQL-Agent-Auftrag Abrufen von Daten aus der Quelle und Einfügen direkt in SQL Server und so zusätzlichen Client-Hop (bessere Leistung).<br /><br />**Im Modus Standard**:  Client-Seite-Migration Datenmodul<br /><br />**Vollständige**:  Client-Seite-Migration Datenmodul<br /><br />**Vollständiger Modus**:  Client-Seite-Migration Datenmodul|  
  
> [!IMPORTANT]  
> Wenn die **Migrationsmodul** Option wird festgelegt, um **Servermodul für die Migration von Seite Daten**, ein neues Projekt, das Festlegen der Option **verwenden 32-Bit-Server-Seite-Migration-Datenmodul** angezeigt wird . Es gibt an, ob es sich bei 32-Bit oder 64-Bit-Windows-Verwaltungsinstrumentation (Bulk Copy Program, BCP)-Hilfsprogramm zum Migrieren von Daten verwendet wird.  
  
### <a name="misc"></a>Sonstiges  
  
|Begriff|Definition|  
|--------|--------------|  
|**Erweiterte Daten Migrationsoptionen**|Zeigt zusätzliche Daten Migrationsoptionen für jede Tabelle in separate detailregisterkarte.<br /><br />**Im Modus Standard**:  Ausblenden<br /><br />**Vollständige**:  Ausblenden<br /><br />**Vollständiger Modus**:  Ausblenden|  
|**On Error**|Die Datenmigration beendet, wenn ein Fehler auftritt. Es gibt drei Optionen:<br /><br />**Beenden Sie Migration:** Daten-Migrationsvorgang beendet<br /><br />**Gehen Sie zur nächsten Tabelle:** Beendet die Datenmigration für die aktuelle Tabelle und geht zur nächsten<br /><br />**Fahren Sie mit dem nächsten Batch fort:** Migration von Daten zu den aktuellen Batch beendet und geht zur nächsten<br /><br />**Im Modus Standard**: Fahren Sie mit dem nächsten Batch fort<br /><br />**Vollständige**: Fahren Sie mit dem nächsten Batch fort<br /><br />**Vollständiger Modus**: Fahren Sie mit dem nächsten Batch fort|  
  
### <a name="parallel-data-migration"></a>Parallele Datenmigration  
  
|Begriff|Definition|  
|--------|--------------|  
|**Parallel Data Migration-Modus**|Gibt den Modus für Verzweigung Threads verwendet werden, um parallele Datenmigration zu aktivieren. Im Auto-Modus wählt SSMA für die Anzahl von Threads (standardmäßig 10), verzweigt haben, um Daten zu migrieren. Im benutzerdefinierten Modus kann Benutzer angeben, die Anzahl der Threads, die zum Migrieren von Daten verzweigt (Mindestwert ist 1, und der Höchstwert ist 100). Derzeit unterstützt nur Client-Seite-Migration Datenmodul parallele Datenmigration.<br /><br />**Im Modus Standard**:  Auto<br /><br />**Vollständige**:  Auto<br /><br />**Vollständiger Modus**:  Auto|  
  
> [!IMPORTANT]  
> Wenn die **Parallel Data Migration-Modus** Option wird festgelegt, um **benutzerdefinierte**, ein neues Projekt, das Festlegen der Option **Threadanzahl** wird angezeigt. Es gibt die Anzahl von Threads, die für die Migration von Daten verwendet.  
  
### <a name="spatial-data"></a>Räumliche Daten  
  
|Begriff|Definition|  
|--------|--------------|  
|**Behandlung von Fehlern**|Gibt an, wie Fehler bei der Migration der Werte der Typen von räumlichen Daten zu behandeln. Wenn 'Ersetzen durch NULL' angegeben ist, werden alle räumlichen Werte, die Fehler verursachen durch NULL ersetzt. Kein Ersatz andernfalls geschieht.<br /><br />**Im Modus Standard**:  Generiert einen Fehler<br /><br />**Vollständige**:  Generiert einen Fehler<br /><br />**Vollständiger Modus**:  Generiert einen Fehler|  
|**Wert-Überprüfung**|Gibt an, wie ungültige räumliche Werte behandelt werden. Wenn 'Versuchen Sie es stellen gültige' angegeben ist, wird ein Versuch unternommen wird, so ändern Sie ungültige Werte, damit sie gültig ist.<br /><br />**Im Modus Standard**: Stellen Sie gültige<br /><br />**Vollständige**: Ändern Sie nicht<br /><br />**Vollständiger Modus**: Stellen Sie gültige|  
  
