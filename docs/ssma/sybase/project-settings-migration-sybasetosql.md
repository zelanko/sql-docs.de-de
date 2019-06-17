---
title: Project Settings (Migration) (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 82f8857f-7ab1-4738-ab6e-b1e95ea94924
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 442212b30f220960f86481f0638c6c12c17da270
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62504078"
---
# <a name="project-settings-migration-sybasetosql"></a>Projekteinstellungen (Migration) (SybaseToSQL)
Der Seite für die Migration von der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA Daten aus Sybase Adaptive Server Enterprise (ASE) migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Im Bereich für die Migration steht in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Zum Angeben von Einstellungen für alle SSMA-Projekten auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden,  **Migration Zielversion** öffnen Sie auf die Dropdownliste **allgemeine** am unteren Rand der linken Bereich ein, und klicken Sie dann auf **Migration**.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand im linken Bereich, und klicken Sie dann auf **Migration**.  
  
## <a name="date-correction-options"></a>Optionen für die Korrektur von Datum  
  
|Begriff|Definition|  
|--------|--------------|  
|**Ersetzen Sie dies nicht unterstützte Datumswerte**|Gibt an, ob SSMA Datumsangaben beheben sollte, die älter als Frühestes unterstütztes sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **"DateTime"** Datum (01 Januar 1753).<br /><br />Um das aktuelle Datum zu erhalten, wählen Sie **nichts**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datumsangaben vor dem 01 Januar 1753 wird in eine Datetime-Spalte nicht akzeptiert werden. Wenn Sie ältere Daten verwenden, müssen Sie die Datums-/ Uhrzeitwerten in Zeichenwerten enthalten, die konvertieren.<br /><br />Wählen Sie zum Konvertieren von Datumsangaben vor dem 01 Januar 1753 auf NULL **durch NULL Ersetzen**.<br /><br />Um Datumsangaben vor dem 01 Januar 1753 mit einem unterstützten Datum ersetzen möchten, wählen Sie **ersetzen Sie dies durch nächste unterstützte Datum**.<br /><br />**Im Modus Standard**:  Keine Aktion durchführen<br /><br />**Vollständige**:  Keine Aktion durchführen<br /><br />**Vollständiger Modus**:  Ersetzen Sie dies durch nächste unterstützte Datum|  
  
## <a name="migration-engine"></a>Ein Migrationsmodul  
  
|Begriff|Definition|  
|--------|--------------|  
|**Ein Migrationsmodul**|Gibt an, während der Datenmigration, verwendet Datenbank-Engine. Client-Side-Datenmigration bezieht sich auf SSMA-Client zum Abrufen der Daten aus der Quelle und die masseneinfügung von Daten in SQL Server. Datenmigration für Server-Seite bezieht sich auf SSMA Data Migration-Engine (Bulk Copy Program) auf das SQL Server als SQL-Agent-Auftrag Abrufen von Daten aus der Quelle und Einfügen direkt in SQL Server und so zusätzlichen Client-Hop (bessere Leistung).<br /><br />**Im Modus Standard**:  Client-Seite-Migration Datenmodul<br /><br />**Vollständige**:  Client-Seite-Migration Datenmodul<br /><br />**Vollständiger Modus**:  Client-Seite-Migration Datenmodul|  
  
> [!IMPORTANT]  
> Wenn die **Migrationsmodul** Option wird festgelegt, um **Servermodul für die Migration von Seite Daten**, ein neues Projekt, das Festlegen der Option **verwenden 32-Bit-Server-Seite-Migration-Datenmodul** angezeigt wird . Es gibt an, ob es sich bei 32-Bit oder 64-Bit-Windows-Verwaltungsinstrumentation (Bulk Copy Program, BCP)-Hilfsprogramm zum Migrieren von Daten verwendet wird.  
  
## <a name="miscellaneous-options"></a>Sonstige Optionen  
  
|Begriff|Definition|  
|--------|--------------|  
|**Batchgröße**|Gibt den Batch Größe, die während der Migration von Daten verwendet.<br /><br />**Im Modus Standard**:  10000<br /><br />**Vollständige**:  10000<br /><br />**Vollständiger Modus**:  10000|  
|**Check-Einschränkungen**|Gibt an, ob SSMA Einschränkungen überprüft werden sollen, wenn sie Daten in SQL Server-Tabellen einfügt.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
|**Data Migration-Timeout**|Gibt das Timeout verwendet wird, während der Datenmigration<br /><br />**Im Modus Standard**:  15<br /><br />**Vollständige**:  15<br /><br />**Vollständiger Modus**:  15|  
|**Erweiterte Daten Migrationsoptionen**|Zeigt zusätzliche Daten Migrationsoptionen für jede Tabelle in separate detailregisterkarte.<br /><br />**Im Modus Standard**:  Ausblenden<br /><br />**Vollständige**:  Ausblenden<br /><br />**Vollständiger Modus**:  Ausblenden|  
|**Trigger auslösen**|Gibt an, ob SSMA einfügen Trigger ausgelöst werden soll, wenn sie Daten in SQL Server-Tabellen hinzufügt.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
|**Identität beibehalten**|Gibt an, ob SSMA Sybase-Identity-Werte beibehält, wenn Daten mit SQL Server hinzugefügt. Der Wert "false" bewirkt, dass Identitätswerte vom Ziel zugewiesen werden soll.<br /><br />**Im Modus Standard**:  Wahr<br /><br />**Vollständige**:  Wahr<br /><br />**Vollständiger Modus**:  Wahr|  
|**NULL-Werte beibehalten**|Gibt an, ob SSMA behält null-Werte in den Quelldaten aus, wenn Daten in SQL Server – unabhängig von den Standardwerten hinzugefügt, die in SQL Server angegeben werden.<br /><br />**Im Modus Standard**:  Wahr<br /><br />**Vollständige**:  Wahr<br /><br />**Vollständiger Modus**:  Wahr|  
|**On Error**|Die Datenmigration beendet, wenn ein Fehler auftritt. Es gibt drei Optionen:<br /><br />**Beenden Sie Migration:** Daten-Migrationsvorgang beendet<br /><br />**Gehen Sie zur nächsten Tabelle:** Beendet die Datenmigration für die aktuelle Tabelle und geht zur nächsten<br /><br />**Fahren Sie mit dem nächsten Batch fort:** Migration von Daten zu den aktuellen Batch beendet und geht zur nächsten<br /><br />**Im Modus Standard**: Fahren Sie mit dem nächsten Batch fort<br /><br />**Vollständige**: Fahren Sie mit dem nächsten Batch fort<br /><br />**Vollständiger Modus**: Fahren Sie mit dem nächsten Batch fort|  
|**Round Bruchteil von Zahlen**|Gibt an, ob kürzen die Sekundenbruchteile von decimal- und numeric-Daten während der Migration zu Integer-Typen oder Fehlermeldung angezeigt, wenn Teil mit Bruchzahlen nicht trivialen ist<br /><br />**Im Modus Standard**:  Nein<br /><br />**Vollständige**:  Nein<br /><br />**Vollständiger Modus**:  Nein|  
|**Sybase-Unicode-Endian**|Gibt den endian Typ für die Sybase-Unicode-Zeichenfolgen. Die folgenden Optionen können für diese Einstellung festgelegt werden:<br /><br />Little-Endian-<br /><br />Big-endian<br /><br />**Im Modus Standard**:  Little-Endian-<br /><br />**Vollständige**:  Little-Endian-<br /><br />**Vollständiger Modus**:  Little-Endian-|  
|**Tabellensperre**|Gibt an, ob es sich bei SSMA Tabellen sperrt, wenn sie Daten in Tabellen während der Datenmigration hinzufügt. Ruft eine Massenaktualisierungssperre für die Dauer des Massenkopiervorgangs ab. Wenn der Wert "false" ist, wird eine Sperre auf Zeilenebene festgelegt.<br /><br />**Im Modus Standard**:  Wahr<br /><br />**Vollständige**:  Wahr<br /><br />**Vollständiger Modus**:  Wahr|  
|**Verwenden von Cursorn**|Die Daten werden abgerufen, aus der Quelldatenbank Cursor verwenden, wenn diese Option festgelegt ist.<br /><br />**Im Modus Standard**:  False<br /><br />**Vollständige**:  False<br /><br />**Vollständiger Modus**:  False|  
  
## <a name="parallel-data-migration"></a>Parallele Datenmigration  
  
|Begriff|Definition|  
|--------|--------------|  
|**Parallel Data Migration-Modus**|Gibt den Modus für Verzweigung Threads verwendet werden, um parallele Datenmigration zu aktivieren. Im Auto-Modus wählt SSMA für die Anzahl von Threads (standardmäßig 10), verzweigt haben, um Daten zu migrieren. Im benutzerdefinierten Modus kann Benutzer angeben, die Anzahl der Threads, die zum Migrieren von Daten verzweigt (Mindestwert ist 1, und der Höchstwert ist 100). Derzeit unterstützt nur Client-Seite-Migration Datenmodul parallele Datenmigration.<br /><br />**Im Modus Standard**:  Auto<br /><br />**Vollständige**:  Auto<br /><br />**Vollständiger Modus**:  Auto|  
  
> [!IMPORTANT]  
> Wenn die **Parallel Data Migration-Modus** Option wird festgelegt, um **benutzerdefinierte**, ein neues Projekt, das Festlegen der Option **Threadanzahl** wird angezeigt. Es gibt die Anzahl von Threads, die für die Migration von Daten verwendet.  
  
