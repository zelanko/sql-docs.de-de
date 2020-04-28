---
title: Verwenden von Test Depots (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a94bd053dac04c4d595e4f2077c02d1d79858e56
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020846"
---
# <a name="using-test-repositories-sybasetosql"></a>Verwenden von Testrepositorys (SybaseToSQL)
Das SSMA-testrepository speichert Testfälle und Testergebnisse für SSMA-Tester für die spätere Verwendung. Die Repository-Daten werden in den SQL Server Tabellen **testcaserepository** und **runtestcaseresultrepository** im Schema **ssma_sybase_utilities** der **ssmatesterdb_syb** Datenbank gespeichert.  
  
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
  
-   Klicken Sie auf die Schaltfläche **Ausführen** , um das Dialogfeld [Testfälle &#40;sybasetosql&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md) ausführen zu öffnen, und führen Sie den ausgewählten Test aus.  
  
## <a name="test-results-repository"></a>Testergebnisse Repository  
Sie können das Testergebnisse-Repository auf der Seite **Testergebnisse** im **Repository des Fensters Test Fälle** anzeigen. Öffnen Sie die Datei, indem Sie im Menü **Tester** auf **Testergebnisse...** klicken.  
  
Auf **Testergebnisse** Seite können Sie zwei Filter verwenden:  
  
-   Der Filter für den Testfall-Namen: ermöglicht die Auswahl von Testergebnissen nach Testfall Namen. Der **gesamte Testfall** -Wert dieses Filters ermöglicht das Anzeigen von Testergebnissen für alle Testfälle.  
  
-   Der Filter für den Testfall-Ausführungs Datum: filtert Testergebnisse nach dem Datum der Speicherung. Der Wert für den **gesamten Zeitraum** des Filters ermöglicht das Anzeigen von Testergebnissen für jedes Datum der Speicherung.  
  
Die folgenden Informationen zu den Testergebnissen werden im Raster angezeigt.  
  
-   Name: der Name des Testfalls.  
  
-   Started: das Testfall-Datum der Ausführung.  
  
-   Ergebnis: eine kurze Zusammenfassung der Testausführung (die QuickInfo der Zelle zeigt eine vollständige Zusammenfassung der Testausführung).  
  
Die folgenden Schaltflächen sind auf der Seite "Test Ergebnisse" verfügbar:  
  
-   Klicken Sie auf die Schaltfläche **anzeigen** , um die [Anzeige von Test Fall berichten &#40;sybasetosql&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) des aktuellen Test Fall Ergebnisses zu öffnen.  
  
-   Klicken Sie auf die Schaltfläche **Löschen** , um das ausgewählte Test Ergebnis zu löschen  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Test Fällen &#40;sybaseto SQL-&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
