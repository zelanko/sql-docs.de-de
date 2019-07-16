---
title: Auswählen und Konfigurieren von Objekten mit Test (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Parameter Comparision Setting
- Tester Component,Selecting Objects
ms.assetid: 89c23aad-bfee-4917-bc16-175288390ac0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2951d4c3bf1eae73ffd066d796b0e3dda4d28cf6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020963"
---
# <a name="selecting-and-configuring-objects-to-test-sybasetosql"></a>Auswählen und Konfigurieren von zu testenden Objekten (SybaseToSQL)
In diesem Schritt wählen Sie die Objekte zu testen, und Konfigurieren von Einstellungen für den Vergleich von Prozeduren und Funktionen Output-Parameter, als auch die Rückgabewerte von Funktionen.  
  
## <a name="selection-of-objects-to-test"></a>Auswahl von Objekten für Test  
Überprüfen Sie in der Sybase-Objektstruktur befindet sich auf der linken Seite des Fensters die Objekte, die Sie während der Tests aufrufen möchten. Die vollständige Liste der getestet werden Objekte in der [migriert Datenbankobjekte testen &#40;SybaseToSQL&#41; ](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md) Thema.  
  
Wenn SSMA Tester die Objekte, die zu Testzwecken ausgewählt nicht unterstützt wird, sehen Sie den Link, mit der Bezeichnung **einige ausgewählte Objekte enthalten Fehler** unter der Objektstruktur. Klicken Sie auf diesen Link an die Gründe, warum diese Objekte nicht getestet werden kann, und um die Auswahl der falschen Objekte zu löschen.  
  
Klicken Sie auf der rechten Seite können Sie mehrere Seiten anzeigen der **SQL** Seite zeigt die Definition für das aktuelle Objekt. In der **Pre SQL** und **Post SQL** Seiten können Skripts, die vor und nach dem Aufruf der startet der Test-Objekt ausgeführt werden sollen. Dies ist möglicherweise nützlich sein, wenn das Objekt zusätzliches Objekt eine solche temporäre Tabellen oder Cursor erfordert. Die **Parameter** Seite listet die Parameter auf, wenn das Objekt eine gespeicherte Prozedur oder eine Funktion ist. Die **Eigenschaften** Seite zeigt zusätzliche Eigenschaften des Objekts. Siehe die Beschreibung der **Parameter Comparsions** und **rufen Werte** nachfolgenden Seiten.  
  
## <a name="parameter-comparison-settings"></a>Vergleich der Parametereinstellungen  
Einrichten der Vergleichsregeln für Output-Parameter und Rückgabewerte in der **Parameter vergleichen** Seite. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-comparisons"></a>Verwendung während der Vergleiche  
Aktivieren Sie die von den ausgewählten Parameter in Vergleichsberichte für Ergebnisse.  
  
-   Auf Wunsch **"true"** , SSMA wird nach dem Ausführen der Prozedur für Sybase mit den entsprechenden Wert auf den Ausgabewert dieses Parameters vergleichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Auf Wunsch **"false"** , der Parameter aus Ergebnisse Überprüfung ausgeschlossen werden.  
  
### <a name="use-custom-scale"></a>Verwenden Sie benutzerdefinierte Skalierung  
Für die Parameter der ungefähren und feste Länge numerischen Datentyp aufweisen können Sie festlegen, dass eine benutzerdefinierte Skalierung für den Vergleich.  
  
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
Sie können die Werte der Eingabeparameter angeben, auf die **rufen Werte** Seite. Die **Aufruf hinzufügen** Schaltfläche wird einen neuen Aufruf mit leeren Werten hinzugefügt. Die **entfernen aufrufen** Schaltfläche entfernt den aktuellen Aufruf.  
  
## <a name="next-step"></a>Nächster Schritt  
[Auswählen und Konfigurieren von betroffenen Objekten &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
