---
title: Auswählen und Konfigurieren von Objekten mit Test (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Selection of Objects to Test,Parameter Comparison Settings
ms.assetid: 29fb6542-5c1f-4b14-a822-87700beb7623
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: d568d1749cd54796072a108e438e448bf2a74578
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62626205"
---
# <a name="selecting-and-configuring-objects-to-test-oracletosql"></a>Auswählen und Konfigurieren von zu testenden Objekten (OracleToSQL)
In diesem Schritt wählen Sie die Objekte zu testen, und Konfigurieren von Einstellungen für den Vergleich von Prozeduren und Funktionen Output-Parameter, als auch die Rückgabewerte von Funktionen.  
  
## <a name="selection-of-objects-to-test"></a>Auswahl von Objekten für Test  
Überprüfen Sie in der Oracle-Objektstruktur befindet sich auf der linken Seite des Fensters die Objekte, die Sie während der Tests aufrufen möchten. Die vollständige Liste der getestet werden Objekte in der [migriert Datenbankobjekte testen &#40;OracleToSQL&#41; ](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md) Thema.  
  
Wenn SSMA Tester die Objekte, die zu Testzwecken ausgewählt nicht unterstützt wird, sehen Sie den Link, mit der Bezeichnung **einige ausgewählte Objekte enthalten Fehler** unter der Objektstruktur. Klicken Sie auf diesen Link an die Gründe, warum diese Objekte nicht getestet werden kann, und um die Auswahl der falschen Objekte zu löschen.  
  
Klicken Sie auf der rechten Seite können Sie mehrere Seiten anzeigen der **SQL** Seite zeigt die Definition für das aktuelle Objekt. Die **Parameter** Seite listet die Parameter auf, wenn das Objekt eine gespeicherte Prozedur oder eine Funktion ist. Die **Eigenschaften** Seite zeigt zusätzliche Eigenschaften des Objekts. Siehe die Beschreibung der **Parameter Vergleiche** und **rufen Werte** nachfolgenden Seiten.  
  
## <a name="parameter-comparison-settings"></a>Vergleich der Parametereinstellungen  
Einrichten der Vergleichsregeln für Output-Parameter und Rückgabewerte in der **Parameter Vergleiche** Seite. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-test-comparisons"></a>Verwendung während der Testvergleiche  
Aktivieren Sie die von den ausgewählten Parameter in Vergleichsberichte für Ergebnisse.  
  
-   Auf Wunsch **"true"** , SSMA wird den Ausgabewert dieses Parameters vergleichen, nach dem Ausführen der Prozedur für Oracle mit dem entsprechenden Wert in SQL Server.
  
-   Auf Wunsch **"false"** , der Parameter aus Ergebnisse Überprüfung ausgeschlossen werden.  
  
### <a name="use-custom-scale"></a>Verwenden Sie benutzerdefinierte Skalierung  
Für die Parameter des numerischen Datentyp aufweisen können Sie festlegen, dass eine benutzerdefinierte Skalierung für den Vergleich.  
  
-   Auf Wunsch **"true"** , numerische Werte entsprechend aufgerundet der **vergleichen Skalierung** Wert, bevor sie verglichen werden.  
  
-   Auf Wunsch **"false"** , exakten numerischen Vergleichs werden.  
  
### <a name="comparing-scale"></a>Vergleichen von Skala  
Nur verfügbar, wenn die **Verwenden benutzerdefinierter Maßstab** Option wird festgelegt, um **"true"** . Dies ist die Genauigkeit für einen numerischen Vergleich.  
  
### <a name="date-time-comparing"></a>Datum Uhrzeit vergleichen  
Definiert, wie die Datum/Uhrzeit-Werte verglichen.  
  
-   Bei Auswahl von **gesamte Datum vergleichen**, vollständigen Vergleich von Werten aus beiden Plattformen ausgeführt werden.  
  
-   Bei Auswahl von **nur Date vergleichen**, wird die Uhrzeit, die Teil ignoriert werden.  
  
-   Bei Auswahl von **vergleichen nur Zeit**, das Datum Teil ignoriert werden.  
  
-   Bei Auswahl von **ignorieren Millisekunden**, bis zu Sekunden werden die Ergebnisse verglichen werden.  
  
-   Bei Auswahl von **ignorieren von Datum und die Millisekunden**, das Ergebnis wird im Vergleich nur vom Time-Teil und wird ignoriert. Bruchteile einer Sekunde sein.  
  
### <a name="ignore-strings-case"></a>Zeichenfolgen Groß-/Kleinschreibung ignorieren  
Steuert den Vergleich die Groß-/Kleinschreibung beachtet.  
  
-   Auf Wunsch **"true"** , der Vergleich wird Groß-/Kleinschreibung sein.  
  
-   Auf Wunsch **"false"** , der Vergleich wird Groß-/Kleinschreibung beachtet werden.  
  
### <a name="ignore-trailing-spaces"></a>Nachfolgende Leerzeichen ignorieren  
Steuert, wie nachfolgende Leerzeichen werden während des Vergleichs behandelt.  
  
-   Auf Wunsch **"true"** , die verglichenen Zeichenfolgen werden vor dem Vergleich werden rechts abgeschnitten.  
  
-   Auf Wunsch **"false"** , behält die verglichenen Zeichenfolgen nachstehende Leerzeichen.  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>Geben Sie die Eingabewerte für die Prozeduren und Funktionen (rufen Sie Werte)  
Sie können die Werte der Eingabeparameter angeben, auf die **rufen Werte** Seite. Die **Aufruf hinzufügen** Schaltfläche wird einen neuen Aufruf mit leeren Werten hinzugefügt. Die **entfernen Aufrufe** Schaltfläche entfernt den aktuellen Aufruf.  
  
## <a name="next-step"></a>Nächster Schritt  
[Auswählen und Konfigurieren von betroffenen Objekten &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
