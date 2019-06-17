---
title: Auswählen und Konfigurieren von betroffenen Objekten (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Columns Comparison Settings
- Selection of Affected Objects
ms.assetid: 545eeda2-9829-4187-a858-619a96b4b71d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: fbd151b0fa8682865e44615c22a9fdd7577014ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62626524"
---
# <a name="selecting-and-configuring-affected-objects-oracletosql"></a>Auswählen und Konfigurieren von betroffenen Objekten (OracleToSQL)
Auf dieser Seite können Sie Tabellen auswählen und die foreign key, Änderungen in der verglichen werden soll, wenn SSMA wird überprüft, die Ergebnisse der Ausführung für die Objekte, die im vorherigen Schritt ausgewählt ob. Darüber hinaus können Sie die Überprüfung der Parameter anpassen.  
  
## <a name="selection-of-affected-objects"></a>Auswahl von betroffenen Objekten  
In der Oracle-Objektstruktur befindet sich auf der linken Seite des Fensters, überprüfen Sie die Tabellen und Fremdschlüssel, Änderungen in der für das gleiche verglichen werden soll.  
  
Wenn der SSMA-Tester keines dieser Objekte überprüfen können, sehen Sie den Link, mit der Bezeichnung **einige ausgewählte Objekte enthalten Fehler** unter der Objektstruktur. Klicken Sie auf diesen Link an die Gründe, warum diese Objekte nicht verglichen werden können, und um die Auswahl der falschen Objekte zu löschen.  
  
## <a name="table"></a>Tabelle  
Die Registerkarte der Tabelle enthält die Rasteransicht der ausgewählten Tabelle an. Das Raster enthält die folgende Informationen über die ausgewählte Tabelle an:  
  
-   Spaltenname  
  
-   Datentyp  
  
-   Genauigkeit  
  
-   Dezimalstellen  
  
-   Rule  
  
-   Default  
  
-   Identität  
  
-   NULL zulassen  
  
## <a name="sql"></a>Sql  
Registerkarte "SQL" enthält die Tabelle"erstellen" SQL der ausgewählten Tabelle.  
  
## <a name="data"></a>Daten  
Registerkarte "Daten" zeigt Daten in die ausgewählte Tabelle an.  
  
## <a name="properties"></a>Eigenschaften  
Registerkarte "Eigenschaften" zeigt die Eigenschaften der ausgewählten Tabelle an. Die folgenden Felder befinden sich unter der Registerkarte "Eigenschaften":  
  
-   Erstellt oder zuletzt geändert  
  
-   Objektnamen  
  
## <a name="columns-comparison-settings"></a>Einstellungen für Spalten Schwellenwertvergleich  
Die Vergleichsregeln für Tabellenspalten herzustellen, auf **Spalten Vergleich** Seite. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-test-comparisons"></a>Verwendung während der Testvergleiche  
Bestimmt, ob diese Spalte in der Ergebnisse testüberprüfung einbezogen werden.  
  
-   Auf Wunsch **"true"** , SSMA wird der Inhalt dieses Artikels vergleichen, nach dem Ausführen des Tests auf Oracle mit dem Inhalt der Spalte in SQL Server. 
  
-   Auf Wunsch **"false"** , von der Überprüfung der Ergebnisse die Spalte ausgeschlossen werden.  
  
### <a name="use-custom-scale"></a>Verwenden Sie benutzerdefinierte Skalierung  
Für Spalten vom numerischen Datentyp aufweisen können Sie festlegen, dass eine benutzerdefinierte Skalierung für den Vergleich.  
  
-   Auf Wunsch **"true"** , numerische Werte entsprechend aufgerundet der **vergleichen Skalierung** Wert, bevor sie verglichen werden.  
  
-   Auf Wunsch **"false"** , exakten numerischen Vergleichs werden.  
  
### <a name="comparing-scale"></a>Vergleichen von Skala  
  
-   Nur verfügbar, wenn die **Verwenden benutzerdefinierter Maßstab** Option wird festgelegt, um **"true"** . Dies ist die Genauigkeit für einen numerischen Vergleich.  
  
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
  
-   Auf Wunsch **"false"** , der Vergleich wird Groß-/Kleinschreibung berücksichtigt.  
  
## <a name="comparing-sql"></a>Vergleich von SQL  
Sehen Sie die SELECT-Anweisungen generiert von SSMA-Tester auf die **SQL vergleichen** Seite. Der Tester werden die Resultsets dieser Anweisungen pro Zeile für Zeile verglichen. Jede nächste Zeile von einem Oracle-Resultset sollte gleich in die nächste Zeile des Resultsets die in SQL Server erstellt wurde.
  
Sie können die SELECT-Anweisungen für die benutzerdefinierte Überprüfung bearbeiten. Verwenden Sie zum Speichern der Änderungen in Oracle und SQL Server-Anweisungen die **übernehmen** Schaltflächen unter der Quell- und Ziel-SQL, entsprechend angepasst.  
  
## <a name="next-step"></a>Nächster Schritt  
[Customizing Calls Order anpassen &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Finishing Test Case Preparation beenden &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
[Ausführen von Testfällen &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
