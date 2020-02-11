---
title: Ausführung von Abfrage Optionen (Seite ANSI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: d9a8b5dea5ab90137c95c9ddaf609c63532dd5b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089079"
---
# <a name="query-options-execution-ansi-page"></a>Abfrageausführung (Seite ANSI)
  Verwenden Sie diese Seite, um [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] anzugeben, dass die Abfragen mithilfe aller oder eines Teils der im ISO-Standard (ANSI) angegebenen Einstellungen ausgeführt werden soll.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **ANSI_DEFAULTS festlegen**  
 Wählt alle Standard-ISO-Einstellungen aus. Dieses Feld ist standardmäßig nicht verfügbar, weil nur einige der ISO-Einstellungen konfiguriert sind.  
  
 **SET QUOTED_IDENTIFIER**  
 Schließt Objektbezeichner in Anführungszeichen ein. Diese Option ist standardmäßig aktiviert.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Ermöglicht NULL-Werte für alle benutzerdefinierten Datentypen- oder -spalten, die während einer CREATE TABLE- oder ALTER TABLE-Anweisung (Standardstatus) nicht explizit als NOTNULL festgelegt wurden. Diese Option ist standardmäßig aktiviert.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Diese Option ist standardmäßig nicht aktiviert.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Schließt automatisch alle offenen Cursors (in Übereinstimmung mit ISO), wenn eine Transaktion durchgeführt wird. Wenn diese Einstellung deaktiviert (auf OFF festgelegt) ist, bleiben Cursor über Transaktionsgrenzen hinweg geöffnet und werden nur geschlossen, wenn die Verbindung geschlossen wird oder die Cursor explizit geschlossen werden. Diese Option ist standardmäßig nicht aktiviert.  
  
 **SET ANSI_PADDING**  
 Steuert das Speichern von Werten in der Spalte, wenn die Werte kürzer als die definierte Spaltengröße sind, und das Speichern von Werten mit nachfolgenden Leerzeichen in **char**-, **varchar**-, **binary**- und **varbinary** -Daten. Diese Einstellung betrifft ausschließlich die Definition neuer Spalten. Nachdem die Spalte erstellt wurde, speichert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Werte gemäß der Einstellung, die beim Erstellen der Spalte festgelegt war. Bestehende Spalten sind von späteren Änderungen dieser Einstellung nicht betroffen. Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
 **SET ANSI_WARNINGS**  
 Gibt das ISO-Standardverhalten für verschiedene Fehlerbedingungen an:  
  
-   Wenn dieses Kontrollkästchen aktiviert ist, wird eine Warnmeldung erstellt, wenn NULL-Werte in Aggregatfunktionen (z. B. SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP oder COUNT) auftreten. Bei **OFF**wird keine Warnung ausgegeben.  
  
-   Wenn dieses Kontrollkästchen deaktiviert ist, bewirken Fehler aufgrund einer Division durch null und arithmetische Überlauffehler, dass für die Anweisung ein Rollback ausgeführt und eine Fehlermeldung erstellt wird. Bei OFF bewirken Fehler aufgrund einer Division durch null und arithmetische Überlauffehler, dass NULL-Werte zurückgegeben werden. Das Verhalten, bei dem Fehler aufgrund einer Division durch null oder arithmetische Überlauffehler bewirken, dass NULL-Werte zurückgegeben werden, tritt auf, wenn versucht wird, einen INSERT- oder UPDATE-Vorgang an einer Zeichen-, Unicode- oder Binärspalte auszuführen, wobei die Länge eines neuen Werts die maximale Spaltengröße überschreitet. Wenn **SET ANSI_WARNINGS** auf ON festgelegt ist, wird der INSERT- oder UPDATE-Vorgang gemäß ISO-Standard abgebrochen. Nachfolgende Leerzeichen werden in Zeichenspalten ignoriert, und nachfolgende Nullen werden in Binärspalten ignoriert. Bei OFF werden Daten auf die Spaltengröße abgeschnitten, und die Anweisung wird erfolgreich ausgeführt.  
  
 Diese Option ist standardmäßig aktiviert.  
  
 **SET ANSI_NULLS**  
 Gibt an, dass sich der Gleichheitsoperator (`=`) und der Ungleichheitsoperator (`<>`) bei Verwendung mit NULL-Werten ISO-konform verhalten müssen. Wenn **SET ANSI_NULLS** ausgewählt ist, werden alle Vergleiche mit einem NULL-Wert in Übereinstimmung mit dem Verhalten nach ISO als UNKNOWN ausgewertet. Wenn **SET ANSI_NULLS** nicht ausgewählt ist, werden alle Datenvergleiche mit einem NULL-Wert als TRUE ausgewertet, falls der Datenwert NULL ist. Diese Option ist standardmäßig aktiviert.  
  
 **Auf Standard zurücksetzen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
