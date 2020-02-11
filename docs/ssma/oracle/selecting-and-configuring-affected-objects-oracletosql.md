---
title: Auswählen und Konfigurieren von betroffenen Objekten (oracleto SQL) | Microsoft-Dokumentation
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
manager: shamikg
ms.openlocfilehash: c06fb621cab581e934ba4655ed6507149d109c60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266502"
---
# <a name="selecting-and-configuring-affected-objects-oracletosql"></a>Auswählen und Konfigurieren von betroffenen Objekten (OracleToSQL)
Auf dieser Seite können Sie Tabellen und Fremdschlüssel auswählen, Änderungen, die verglichen werden sollen, wenn SSMA die Ausführungs Ergebnisse für die im vorherigen Schritt ausgewählten Objekte überprüft. Außerdem können Sie die Überprüfungs Parameter anpassen.  
  
## <a name="selection-of-affected-objects"></a>Auswahl betroffener Objekte  
Überprüfen Sie in der Oracle-Objektstruktur, die sich auf der linken Seite des Fensters befindet, die Tabellen und Fremdschlüssel, Änderungen, die als identisch verglichen werden sollen.  
  
Wenn SSMA Tester keines dieser Objekte überprüfen kann, sehen Sie, dass der Link mit der Bezeichnung **einige ausgewählte Objekte** unter der Struktur Objekte Fehler enthält. Klicken Sie auf diesen Link, um die Gründe anzuzeigen, warum diese Objekte nicht verglichen werden können, und um die Auswahl falscher Objekte zu löschen.  
  
## <a name="table"></a>Tabelle  
Die Registerkarte Tabelle enthält die Rasteransicht der ausgewählten Tabelle. Das Raster enthält die folgenden Informationen zur ausgewählten Tabelle:  
  
-   Spaltenname  
  
-   Datentyp  
  
-   Precision  
  
-   Skalieren  
  
-   Regel  
  
-   Standard  
  
-   Identity  
  
-   Nullable  
  
## <a name="sql"></a>Sql  
Die Registerkarte "SQL" enthält die SQL-Tabelle "CREATE TABLE" der ausgewählten Tabelle.  
  
## <a name="data"></a>Data  
Registerkarte Daten zeigt Daten an, die in der ausgewählten Tabelle enthalten sind.  
  
## <a name="properties"></a>Eigenschaften  
Registerkarte "Eigenschaften" zeigt die Eigenschaften der ausgewählten Tabelle an. Die folgenden Felder sind auf der Registerkarte Eigenschaften vorhanden:  
  
-   Erstellt oder zuletzt geändert  
  
-   Objektname  
  
## <a name="columns-comparison-settings"></a>Spalten Vergleichs Einstellungen  
Legen Sie die Vergleichs Regeln für Tabellen Spalten auf der Seite mit den **Spalten vergleichen** fest. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-test-comparisons"></a>Verwendung während der Test Vergleiche  
Bestimmen Sie, ob diese Spalte an der Überprüfung der Testergebnisse beteiligt ist.  
  
-   Wenn Sie **true**auswählen, vergleicht SSMA den Inhalt dieser Spalte nach dem Ausführen des Tests für Oracle mit dem Inhalt der Spalte in SQL Server. 
  
-   Wenn Sie**false**auswählen, wird die Spalte von der Ergebnis Überprüfung ausgeschlossen.  
  
### <a name="use-custom-scale"></a>Benutzerdefinierte Skalierung verwenden  
Für Spalten mit einem numerischen Datentyp können Sie eine benutzerdefinierte Skala für den Vergleich festlegen.  
  
-   Wenn Sie **true**auswählen, werden numerische Werte entsprechend dem **Vergleichs Skalierungs** Wert gerundet, bevor Sie verglichen werden.  
  
-   Wenn Sie**false**auswählen, ist der numerische Vergleich genau.  
  
### <a name="comparing-scale"></a>Vergleichen der Skala  
  
-   Nur verfügbar, wenn die Option **benutzerdefinierte Skalierung verwenden** auf **true**festgelegt ist. Dies ist die Genauigkeit für den numerischen Vergleich.  
  
### <a name="date-time-comparing"></a>Vergleichen von Datum und Uhrzeit  
Definiert, wie Datums-/Uhrzeitwerte verglichen werden.  
  
-   Wenn Sie die Option **gesamtes Datum vergleichen**auswählen, wird ein vollständiger Vergleich der Werte beider Plattformen ausgeführt.  
  
-   Wenn Sie **Datum nur vergleichen**auswählen, wird der Uhrzeit Teil ignoriert.  
  
-   Wenn Sie **nur die Zeit vergleichen**auswählen, wird der Datums Teil ignoriert.  
  
-   Wenn Sie die Option **Millisekunden ignorieren**auswählen, werden die Ergebnisse bis zu Sekunden verglichen.  
  
-   Wenn Sie **Datum und Millisekunden ignorieren**auswählen, wird das Ergebnis nur nach Zeit Teil verglichen, und die Sekundenbruchteile werden ignoriert.  
  
### <a name="ignore-strings-case"></a>Zeichen folgen ignorieren  
Steuert die Groß-/Kleinschreibung des Vergleichs.  
  
-   Wenn Sie **true**auswählen, wird beim Vergleich die Groß-/Kleinschreibung nicht beachtet.  
  
-   Wenn Sie **false**auswählen, wird beim Vergleich der Buchstabe Groß-/Kleinschreibung berücksichtigt.  
  
## <a name="comparing-sql"></a>Vergleichen von SQL  
Sie können die von SSMA Tester generierten SELECT-Anweisungen auf der Seite **SQL vergleichen** anzeigen. Der Tester vergleicht die Resultsets dieser Anweisungen zeilenweise. Jede nächste Zeile eines Oracle-Resultsets sollte gleich der nächsten Zeile des Resultsets sein, das in SQL Server erstellt wurde.
  
Sie können diese SELECT-Anweisungen bearbeiten, um eine benutzerdefinierte Überprüfung bereitzustellen Um die Änderungen in Oracle und in SQL Server-Anweisungen zu speichern, verwenden Sie die **Apply** -Schaltflächen unter dem Quell-und Ziel-SQL entsprechend.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anpassen von Aufruf Reihenfolge &#40;oracleto SQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Fertigstellung der Test Fall Vorbereitung &#40;oracleto SQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
[Ausführen von Test Fällen &#40;oracleto SQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;oracleto SQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
