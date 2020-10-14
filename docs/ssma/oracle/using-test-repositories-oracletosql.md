---
description: Verwenden von Testrepositorys (OracleToSQL)
title: Verwenden von Test Depots (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6b070a45c7990efbb598401b241083fcb2d804f5
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035139"
---
# <a name="using-test-repositories-oracletosql"></a>Verwenden von Testrepositorys (OracleToSQL)
Das SSMA-testrepository speichert Testfälle und Testergebnisse für SSMA-Tester für die spätere Verwendung. Die Repository-Daten werden in den SQL Server Tabellen **testcaserepository** und **runtestcaseresultrepository** im Schema **ssma_oracle_utilities** der **ssmatesterdb** -Datenbank gespeichert.  
  
Die folgenden Schaltflächen sind im Repository des Dialog Felds "Testfälle" verfügbar:  
  
-   Klicken Sie auf die Schaltfläche **Aktualisieren** , um die Testfälle oder Testergebnisse Liste zu aktualisieren.  
  
-   Klicken Sie auf die Schaltfläche **Schließen** , um das Repository des Dialog Felds Testfälle zu schließen.  
  
## <a name="test-cases-repository"></a>Testfälle-Repository  
Sie können das Repository "Testfälle" anzeigen, indem Sie im Menü " **Tester** " auf **Testfälle...** klicken. SSMA zeigt dann das **Repository des** Dialogfensters "Test Fälle" mit einer Liste gespeicherter Testfälle auf der Seite " **Testfälle** " an.  
  
Das Raster zeigt die folgenden Informationen zu den einzelnen Testfällen an:  
  
-   Name: der Name des Testfalls.  
  
-   Erstellt: das Erstellungsdatum für den Testfall.  
  
-   Geändert: das Datum der letzten Änderung des Testfalls.  
  
-   Beschreibung: die Test Fallbeschreibungen.  
  
Die folgenden Schaltflächen sind auf der Seite mit den Test Fällen verfügbar:  
  
-   Klicken Sie auf die Schaltfläche **Hinzufügen** , um den Testfall-Assistenten auszuführen und einen neuen Test zu erstellen.  
  
-   Klicken Sie auf die Schaltfläche **Entfernen** , um den ausgewählten Test aus dem Repository zu löschen. Wenn ein Testfall gelöscht wird, werden alle zugehörigen Testergebnisse ebenfalls gelöscht.  
  
-   Klicken Sie auf die Schaltfläche **Bearbeiten** , um den Testfall-Assistenten auszuführen und den ausgewählten Test zu ändern.  
  
-   Klicken Sie auf die Schaltfläche **Ausführen** , um das Dialogfeld [Testfälle ausführen (oracletosql)](./running-test-cases-oracletosql.md) zu öffnen, und führen Sie den ausgewählten Test aus.  
  
## <a name="test-results-repository"></a>Testergebnisse Repository  
Sie können das Testergebnisse-Repository auf der Seite **Testergebnisse** im **Repository des Fensters Test Fälle** anzeigen. Öffnen Sie die Datei, indem Sie im Menü **Tester** auf **Testergebnisse...** klicken.  
  
Auf **Testergebnisse** Seite können Sie zwei Filter verwenden:  
  
-   Der Filter für den Testfall-Namen: ermöglicht die Auswahl von Testergebnissen nach Testfall Namen. Der Wert für **alle Testfälle** dieses Filters ermöglicht das Anzeigen von Testergebnissen für alle Testfälle.  
  
-   Der Filter für den Testfall-Ausführungs Datum: filtert Testergebnisse nach dem Datum der Speicherung. Der Wert für den **gesamten Zeitraum** des Filters ermöglicht das Anzeigen von Testergebnissen für jedes Datum der Speicherung.  
  
Die folgenden Informationen zu den Testergebnissen werden im Raster angezeigt.  
  
-   Name: der Name des Testfalls.  
  
-   Gespeichert: das Datum der Speicherung von Test Fällen.  
  
-   Ergebnisse: eine kurze Zusammenfassung der Testausführung (die QuickInfo der Zelle zeigt eine vollständige Zusammenfassung der Testausführung).  
  
Die folgenden Schaltflächen sind auf der Seite "Test Ergebnisse" verfügbar:  
  
-   Klicken Sie auf die Schaltfläche **anzeigen** , um die [Anzeige von Test Fall berichten &#40;oracletosql&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) des aktuellen Test Fall Ergebnisses zu öffnen.  
  
-   Klicken Sie auf die Schaltfläche **Löschen** , um das ausgewählte Test Ergebnis zu löschen  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Test Fällen &#40;oracleto SQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;oracleto SQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
