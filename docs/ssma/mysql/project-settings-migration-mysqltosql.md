---
title: Projekteinstellungen (Migration) (mysqlto SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67908867"
---
# <a name="project-settings-migration-mysqltosql"></a>Projekteinstellungen (Migration) (MySqlToSql)
Die Seite Migration des Dialog Felds **Projekteinstellungen** enthält Einstellungen, mit denen Sie anpassen können, wie SSMA Daten von MySQL zu SQL Server migriert.  
  
Der Bereich Migration ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Wenn Sie Einstellungen für alle SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras die Option** **Standard Projekteinstellungen**aus, wählen Sie den Projekttyp in der Dropdown Liste **Migrations Ziel Version** aus, für die Sie auf die Einstellungen zugreifen möchten, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Migration**.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die **Option Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Migration**.  
  
## <a name="options"></a>Optionen  
  
### <a name="bulk-copy"></a>Massen kopieren  
  
|Begriff|Definition|  
|--------|--------------|  
|**Batch Size**|Gibt die Batch Größe an, die während der Datenmigration verwendet wird.<br /><br />**Standardmodus**: 1000<br /><br />**Optimistischer Modus**: 1000<br /><br />**Vollständiger Modus**: 1000|  
|**Check-Einschränkungen**|Gibt an, ob SSMA Einschränkungen überprüfen soll, wenn Daten in SQL Server Tabellen eingefügt werden.<br /><br />**Standardmodus**: false<br /><br />**Optimistischer Modus**: false<br /><br />**Vollständiger Modus**: false|  
|**Trigger auslösen**|Gibt an, ob SSMA Einfügetrigger auslösen soll, wenn Daten SQL Server Tabellen hinzugefügt werden.<br /><br />**Standardmodus**: false<br /><br />**Optimistischer Modus**: false<br /><br />**Vollständiger Modus**: false|  
|**Identität beibehalten**|Gibt an, ob SSMA beim Hinzufügen von Daten zu SQL Server MySQL-Identitäts Werte beibehält. Der Wert false bewirkt, dass Identitäts Werte vom Ziel zugewiesen werden.<br /><br />**Standardmodus**: true<br /><br />**Optimistischer Modus**: true<br /><br />**Vollständiger Modus**: true|  
|**NULL-Werte beibehalten**|Gibt an, ob SSMA beim Hinzufügen von Daten zu SQL Server NULL-Werte in den Quelldaten beibehält, unabhängig von den in SQL Server angegebenen Standardwerten.<br /><br />**Standardmodus**: true<br /><br />**Optimistischer Modus**: true<br /><br />**Vollständiger Modus**: true|  
|**Tabellensperre**|Gibt an, ob SSMA Tabellen sperrt, wenn während der Datenmigration Daten zu Tabellen hinzugefügt werden. Erhält eine Massen Aktualisierungs Sperre für die Dauer des Massen Kopiervorgangs. Wenn der Wert false ist, wird auf Zeilenebene eine Sperre festgelegt.<br /><br />**Standardmodus**: false<br /><br />**Optimistischer Modus**: false<br /><br />**Vollständiger Modus**: false|  
  
### <a name="data-modification"></a>Datenänderung  
  
|Begriff|Definition|  
|--------|--------------|  
|**Migration Ungültiger Datumsangaben**|Gibt an, wie ungültige Datumsangaben mit like "2007-04-23" oder "2000-06-31 10:00:00" in Datums-und DateTime-Formaten migriert werden.<br /><br />**Standardmodus**: NULL festlegen<br /><br />**Optimistischer Modus**: NULL festlegen<br /><br />**Vollständiger Modus**: NULL festlegen|  
|**Migration negativer Zeit Werte**|Gibt an, wie negative Werte wie "-30:11:00" in Zeit Spalten migriert werden.<br /><br />**Standardmodus**: NULL festlegen<br /><br />**Optimistischer Modus**: NULL festlegen<br /><br />**Vollständiger Modus**: NULL festlegen|  
|**Zeitwerte über 24 Stunden Migration**|Gibt an, wie Zeit Werte von mehr als ' 23:59:59 ' in Zeit Spalten migriert werden.<br /><br />**Standardmodus**: NULL festlegen<br /><br />**Optimistischer Modus**: NULL festlegen<br /><br />**Vollständiger Modus**: NULL festlegen|  
|**Kürzen der Binär Werte, um in die Spalte zu passen**|Wenn ja, verkürzt SSMA Binär Werte aus MySQL, die nicht in SQL-Tabellen Spalten passen, und generiert eine entsprechende Fehlermeldung. Wenn Nein, verursacht die Zeile einen Fehler.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollmodus**: Nein|  
|**Abschneiden von Zeichen Werten, die in eine Spalte passen**|SSMA verkürzt Zeichen Werte aus MySQL, die nicht in SQL-Tabellen Spalten passen, und generiert eine entsprechende Fehlermeldung.<br /><br />**Standardmodus**: Nein<br /><br />**Optimistischer Modus**: Nein<br /><br />**Vollmodus**: Nein|  
|**Migration von Zero dates**|Gibt an, wie Datums-und DateTime-Spalten NULL-Datumsangaben wie "0000-00-00" oder "0000-00-00 00:00:00" migriert werden.<br /><br />**Standardmodus**: NULL festlegen<br /><br />**Optimistischer Modus**: NULL festlegen<br /><br />**Vollständiger Modus**: NULL festlegen|  
|**Migration von NULL in Datumsangaben**|Gibt an, wie Datums-und DateTime-Spalten mit NULL Teilen wie "2009-01-00" oder "2000-00-00 11:00:00" migriert werden.<br /><br />**Standardmodus**: NULL festlegen<br /><br />**Optimistischer Modus**: NULL festlegen<br /><br />**Vollständiger Modus**: NULL festlegen|  
  
### <a name="migration-engine"></a>Migrations-Engine  
  
|Begriff|Definition|  
|--------|--------------|  
|**Migrations-Engine**|Gibt die während der Daten Migration verwendete Datenbank-Engine an. Bei der Client seitigen Datenmigration wird der SSMA-Client zum Abrufen der Daten aus der Quelle und zum Massen Einfügen dieser Daten in SQL Server bezeichnet. Die Server seitige Datenmigration bezieht sich auf die SSMA-Datenmigrations-Engine (Massen Kopier Programm), die im SQL Server Feld ausgeführt wird, als SQL-Agentauftrag, der Daten aus der Quelle abruft und direkt in SQL Server einfügt, wodurch ein zusätzlicher Client-Hop (bessere Leistung) vermieden wird.<br /><br />**Standardmodus**: Client seitiges Datenmigrations-Engine<br /><br />**Optimistischer Modus**: Client seitiges Datenmigrations-Engine<br /><br />**Vollständiger Modus**: Client seitiges Datenmigrations-Engine|  
  
> [!IMPORTANT]  
> Wenn die Option **Migrations-Engine** auf **serverseitiges Datenmigrations-Engine**festgelegt ist, wird eine neue Projekt Einstellungs Option **Use 32-Bit Server seitiges Data Migration Engine** angezeigt. Hiermit wird angegeben, ob zum Migrieren von Daten das 32-Bit-oder 64-Bit-Hilfsprogramm für das Massen Kopier Programm verwendet wird.  
  
### <a name="misc"></a>Sonstiges  
  
|Begriff|Definition|  
|--------|--------------|  
|**Erweiterte Daten Migrations Optionen**|Zeigt zusätzliche Daten Migrations Optionen für jede Tabelle auf einer separaten Detail Registerkarte an.<br /><br />**Standardmodus**: Ausblenden<br /><br />**Optimistischer Modus**: Ausblenden<br /><br />**Vollmodus**: Ausblenden|  
|**Bei Fehler**|Beendet die Datenmigration, wenn ein Fehler auftritt. Es gibt drei Optionen:<br /><br />**Migration Abbrechen:** Beendet den Daten Migrations Vorgang.<br /><br />**Weiter zur nächsten Tabelle:** Beendet die Datenmigration zur aktuellen Tabelle und geht zum nächsten<br /><br />**Zum nächsten Batch wechseln:** Beendet die Datenmigration zum aktuellen Batch und geht zum nächsten<br /><br />**Standardmodus**: fahren Sie mit dem nächsten Batch fort<br /><br />**Optimistischer Modus**: mit dem nächsten Batch fortfahren<br /><br />**Vollständiger Modus**: mit dem nächsten Batch fortfahren|  
  
### <a name="parallel-data-migration"></a>Parallele Daten Migration  
  
|Begriff|Definition|  
|--------|--------------|  
|**Paralleler Daten Migrations Modus**|Gibt den Modus an, der zum Verzweigen von Threads verwendet wird, um die parallele Datenmigration Im Auto-Modus wählt SSMA die Anzahl der Threads (standardmäßig 10) aus, die zum Migrieren von Daten verzweigt werden. Im benutzerdefinierten Modus kann der Benutzer die Anzahl der Threads angeben, die für die Datenmigration verzweigt werden sollen (der Minimalwert ist 1 und der Höchstwert 100). Derzeit unterstützt nur die Client seitige Daten Migrations-Engine die parallele Datenmigration.<br /><br />**Standardmodus**: automatisch<br /><br />**Optimistischer Modus**: automatisch<br /><br />**Vollständiger Modus**: automatisch|  
  
> [!IMPORTANT]  
> Wenn die Option " **paralleler Daten Migrations Modus** " auf " **Benutzer**definiert" festgelegt ist, wird eine neue Projekt Einstellungs Option **Thread Anzahl** angezeigt. Gibt die Anzahl von Threads an, die für die Datenmigration verwendet werden.  
  
### <a name="spatial-data"></a>Räumliche Daten  
  
|Begriff|Definition|  
|--------|--------------|  
|**Behandeln von Fehlern**|Gibt an, wie Fehler bei der Migration von Werten räumlicher Datentypen behandelt werden. Wenn ' Replace with NULL ' angegeben ist, werden alle räumlichen Werte, die Fehler verursachen, durch Null ersetzt. Andernfalls wird kein Ersatz ausgeführt.<br /><br />**Standardmodus**: Fehler generieren<br /><br />**Optimistischer Modus**: Fehler generieren<br /><br />**Vollständiger Modus**: Fehler generieren|  
|**Wert Validierung**|Gibt an, wie ungültige räumliche Werte behandelt werden. Wenn "try Make valid" angegeben ist, wird versucht, ungültige Werte zu ändern, damit Sie gültig sind.<br /><br />**Standardmodus**: als gültig festlegen<br /><br />**Optimistischer Modus**: nicht ändern<br /><br />**Vollständiger Modus**: als gültig festlegen|  
  
