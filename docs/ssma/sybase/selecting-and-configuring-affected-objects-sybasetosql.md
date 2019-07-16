---
title: Auswählen und Konfigurieren von betroffenen Objekten (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Affected Objects
ms.assetid: a219df74-543a-4aec-aeeb-79f90ac3e2ee
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3aa7ccc8d559f7017fd2a9bf0bc20bc7ae191c46
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020990"
---
# <a name="selecting-and-configuring-affected-objects-sybasetosql"></a>Auswählen und Konfigurieren von betroffenen Objekten (SybaseToSQL)
Auf dieser Seite können Sie Tabellen auswählen und die foreign key, Änderungen in der verglichen werden soll, wenn SSMA wird überprüft, die Ergebnisse der Ausführung für die Objekte, die im vorherigen Schritt ausgewählt ob. Darüber hinaus können Sie die Überprüfung der Parameter anpassen.  
  
## <a name="selection-of-affected-objects"></a>Auswahl von betroffenen Objekten  
In der Sybase-Objektstruktur befindet sich auf der linken Seite des Fensters, überprüfen Sie die Tabellen und Fremdschlüssel, Änderungen in der für das gleiche verglichen werden soll.  
  
Wenn der SSMA-Tester keines dieser Objekte überprüfen können, sehen Sie den Link, mit der Bezeichnung **einige ausgewählte Objekte enthalten Fehler** unter der Objektstruktur. Klicken Sie auf diesen Link an die Gründe, warum diese Objekte nicht verglichen werden können, und um die Auswahl der falschen Objekte zu löschen.  
  
## <a name="table"></a>Tabelle  
Die Registerkarte der Tabelle enthält die Rasteransicht der ausgewählten Tabelle an. Das Raster enthält die folgende Informationen über die ausgewählte Tabelle an:  
  
-   Spaltenname  
  
-   Datentyp  
  
-   Genauigkeit  
  
-   Dezimalstellen  
  
-   Regel  
  
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
  
## <a name="table-comparison-settings"></a>Einstellungen für Datentabellen Vergleich  
Einrichten der Vergleichsregeln für die Tabelle auf **Tabellenvergleiche** Seite. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="comparison-mode"></a>Vergleichsmodus  
Definiert den Tabelleninhalt auf die werden den Vergleich ausgeführt.  
  
-   Bei Auswahl von **nur geänderte**, vollständigen Vergleich der Tabellenzeilen wird ausgeführt.  
  
-   Bei Auswahl von **vollständige**, erfolgt der Vergleich für nur die Zeilen, die geändert wurden.  
  
## <a name="column-comparison-settings"></a>Vergleich von Spalteneinstellungen  
Die Vergleichsregeln für Tabellenspalten herzustellen, auf **Spalte Vergleiche** Seite. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-test-comparisons"></a>Verwendung während der Testvergleiche  
Bestimmt, ob diese Spalte in der Ergebnisse testüberprüfung einbezogen werden.  
  
-   Auf Wunsch **"true"** , SSMA wird der Inhalt dieses Artikels vergleichen, nach dem Ausführen des Tests auf Sybase mit dem Inhalt der Spalte in SQL Server.
  
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
Sehen Sie die SELECT-Anweisungen generiert von SSMA-Tester auf die **SQL vergleichen** Seite. Der Tester werden die Resultsets dieser Anweisungen pro Zeile für Zeile verglichen. Jede nächste Zeile eines Resultsets Sybase übereinstimmen sollten auf die nächste Zeile des Resultsets in erstellten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Sie können die SELECT-Anweisungen für die benutzerdefinierte Überprüfung bearbeiten. Zum Speichern der Änderungen in Sybase und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anweisungen können mithilfe der **übernehmen** Schaltflächen unter der Quell- und Ziel-SQL, entsprechend angepasst.  
  
## <a name="next-step"></a>Nächster Schritt  
[Customizing Calls Order anpassen &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
