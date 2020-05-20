---
title: Optionen (Abfrage Ausführung-SQL Server-ANSI-Seite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAnsi
ms.assetid: 0f4c6887-0562-417e-806c-b5cffb1e7c5c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23e46eaf73be4f14e90065627379bb778525051a
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000840"
---
# <a name="options-query-execution-sql-server-ansi-page"></a>Optionen (Abfrage Ausführung-SQL Server-ANSI-Seite)
  Diese SET-Optionen nach ANSI (ISO)-Standard definieren zusammen die Abfrageverarbeitungsumgebung für die Dauer der Abfrage des Benutzers bzw. der Ausführung eines Triggers oder einer gespeicherten Prozedur. Die aufgeführten SET-Optionen schließen jedoch nicht alle Optionen ein, die erforderlich wären, um dem ISO-Standard vollständig zu entsprechen. Verwenden Sie diese Seite, um anzugeben, dass [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Abfragen mithilfe aller oder eines Teils der im ISO-Standard angegebenen Einstellungen ausgeführt werden soll. Die an diesen Optionen vorgenommenen Änderungen werden nur für neue Abfragen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet. Um die Optionen für die aktuellen Abfragen zu ändern, klicken Sie im Menü **Abfrage** auf **Abfrage Optionen** , oder klicken Sie mit der rechten Maustaste in das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Abfragefenster, und wählen Sie **Abfrage Optionen**aus. Klicken Sie im Dialogfeld **Abfrageoptionen** unter **Ausführung** auf **ANSI**.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **SET ANSI_DEFAULTS**  
 Aktivieren Sie dieses Kontrollkästchen, um alle ISO-Standardeinstellungen auszuwählen. Nicht alle ISO-Optionen sind standardmäßig ausgewählt.  
  
 **SET QUOTED_IDENTIFIER**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die ISO-Regeln hinsichtlich der doppelten Anführungszeichen zur Begrenzung von Bezeichnern und Zeichenfolgenliteralen beachtet. Bei Bezeichnern, die von Anführungszeichen begrenzt werden, kann es sich um Transact-SQL-Schlüsselwörter oder um Bezeichner mit Zeichen handeln, die nach den Transact-SQL-Syntaxregeln für Bezeichner eigentlich nicht zulässig sind. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Wenn dieser Wert festgelegt wird, sind in allen benutzerdefinierten Datentypen oder Spalten, die in einer CREATE TABLE- oder einer ALTER TABLE-Anweisung nicht explizit als NOT NULL definiert werden, NULL-Werte standardmäßig zulässig. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Wenn dieses Kontrollkästchen aktiviert ist, setzt SET IMPLICIT_TRANSACTIONS die Verbindung in den impliziten Transaktionsmodus. Wenn dieses Kontrollkästchen deaktiviert ist, setzt der Befehl die Verbindung in den Autocommitmodus zurück. Informationen zu den Anweisungen, die eine implizite Transaktion starten, finden Sie unter [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-implicit-transactions-transact-sql). Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden alle geöffneten Cursors automatisch geschlossen (in Übereinstimmung mit ISO), sobald für eine Transaktion ein Commit ausgeführt wurde. Wenn dieser Wert auf OFF festgelegt wurde, bleiben Cursor über Transaktionsgrenzen hinweg geöffnet und werden nur geschlossen, wenn die Verbindung geschlossen wird oder die Cursor explizit geschlossen werden. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SET ANSI_PADDING**  
 Steuert, wie Wertenamen in der Spalte gespeichert werden, wenn die Namen kürzer als die definierte Spaltengröße sind, und wie in der Spalte Werte mit nachfolgenden Leerzeichen in Daten des Typs **char**, **varchar**, **binary**, und **varbinary** gespeichert werden. Diese Einstellung betrifft ausschließlich die Definition neuer Spalten. Nachdem die Spalte erstellt wurde, speichert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Werte gemäß der Einstellung, die beim Erstellen der Spalte festgelegt war. Bestehende Spalten sind von späteren Änderungen dieser Einstellung nicht betroffen. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET ANSI_WARNINGS**  
 Gibt das ISO-Standardverhalten für verschiedene Fehlerbedingungen an:  
  
-   Wenn dieses Kontrollkästchen aktiviert ist, wird eine Warnmeldung erstellt, wenn NULL-Werte in Aggregatfunktionen (z. B. SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP oder COUNT) auftreten. Bei OFF wird keine Warnung ausgegeben.  
  
-   Wenn dieses Kontrollkästchen deaktiviert ist, bewirken Fehler aufgrund einer Division durch null und arithmetische Überlauffehler, dass für die Anweisung ein Rollback ausgeführt und eine Fehlermeldung erstellt wird. Bei OFF bewirken Fehler aufgrund einer Division durch null und arithmetische Überlauffehler, dass NULL-Werte zurückgegeben werden. Das Verhalten, bei dem Fehler aufgrund einer Division durch null oder arithmetische Überlauffehler bewirken, dass NULL-Werte zurückgegeben werden, tritt auf, wenn ein INSERT- oder UPDATE-Vorgang in einer Spalte des Typs **character**, **Unicode** oder **binary** versucht wird und die Länge eines der neuen Werte die maximale Spaltengröße überschreitet. Wenn SET ANSI_WARNINGS auf ON festgelegt ist, wird der INSERT- oder UPDATE-Vorgang gemäß ISO-Standard abgebrochen. Nachfolgende Leerzeichen werden in Zeichenspalten ignoriert, und nachfolgende Nullen werden in Binärspalten ignoriert. Bei OFF werden Daten auf die Spaltengröße abgeschnitten, und die Anweisung wird erfolgreich ausgeführt.  
  
 Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET ANSI_NULLS**  
 -   Gibt an, dass sich die Vergleichsoperatoren gleich (=) und ungleich (<>) bei Verwendung mit NULL-Werten ISO-konform verhalten müssen. Wenn SET ANSI_NULLS ausgewählt ist, werden alle Vergleiche mit null in Übereinstimmung mit dem Verhalten nach ISO als UNKNOWN ausgewertet. Wenn SET ANSI_NULLS nicht ausgewählt ist, werden Vergleiche aller Daten mit einem NULL-Wert als TRUE ausgewertet. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **Standard wiederherstellen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
