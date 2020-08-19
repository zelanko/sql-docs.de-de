---
description: Auswählen und Konfigurieren von betroffenen Objekten (SybaseToSQL)
title: Auswählen und konfigurieren betroffener Objekte (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Affected Objects
ms.assetid: a219df74-543a-4aec-aeeb-79f90ac3e2ee
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 793430d548053b8d4c1cbf8dd07dd4e7d691c6d3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468742"
---
# <a name="selecting-and-configuring-affected-objects-sybasetosql"></a>Auswählen und Konfigurieren von betroffenen Objekten (SybaseToSQL)
Auf dieser Seite können Sie Tabellen und Fremdschlüssel auswählen, Änderungen, die verglichen werden sollen, wenn SSMA die Ausführungs Ergebnisse für die im vorherigen Schritt ausgewählten Objekte überprüft. Außerdem können Sie die Überprüfungs Parameter anpassen.  
  
## <a name="selection-of-affected-objects"></a>Auswahl betroffener Objekte  
Überprüfen Sie in der Sybase-Objektstruktur, die sich auf der linken Seite des Fensters befindet, die Tabellen und Fremdschlüssel, Änderungen, die als identisch verglichen werden sollen.  
  
Wenn SSMA Tester keines dieser Objekte überprüfen kann, sehen Sie, dass der Link mit der Bezeichnung **einige ausgewählte Objekte** unter der Struktur Objekte Fehler enthält. Klicken Sie auf diesen Link, um die Gründe anzuzeigen, warum diese Objekte nicht verglichen werden können, und um die Auswahl falscher Objekte zu löschen.  
  
## <a name="table"></a>Tabelle  
Die Registerkarte Tabelle enthält die Rasteransicht der ausgewählten Tabelle. Das Raster enthält die folgenden Informationen zur ausgewählten Tabelle:  
  
-   Spaltenname  
  
-   Datentyp  
  
-   Genauigkeit  
  
-   Skalieren  
  
-   Regel  
  
-   Standard  
  
-   Identity  
  
-   Nullable  
  
## <a name="sql"></a>Sql  
Die Registerkarte "SQL" enthält die SQL-Tabelle "CREATE TABLE" der ausgewählten Tabelle.  
  
## <a name="data"></a>Daten  
Registerkarte Daten zeigt Daten an, die in der ausgewählten Tabelle enthalten sind.  
  
## <a name="properties"></a>Eigenschaften  
Registerkarte "Eigenschaften" zeigt die Eigenschaften der ausgewählten Tabelle an. Die folgenden Felder sind auf der Registerkarte Eigenschaften vorhanden:  
  
-   Erstellt oder zuletzt geändert  
  
-   Objektname  
  
## <a name="table-comparison-settings"></a>Tabellen Vergleichs Einstellungen  
Legen Sie die Vergleichs Regeln für die Tabelle auf der Seite **Vergleiche** fest. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="comparison-mode"></a>Vergleichs Modus  
Definiert den Tabelleninhalt, für den der Vergleich durchgeführt wird.  
  
-   Wenn Sie **nur Änderungen**auswählen, wird ein vollständiger Vergleich der Tabellenzeilen ausgeführt.  
  
-   Wenn Sie **vollständig**auswählen, wird der Vergleich nur für die geänderten Zeilen ausgeführt.  
  
## <a name="column-comparison-settings"></a>Spalten Vergleichs Einstellungen  
Legen Sie die Vergleichs Regeln für Tabellen Spalten auf der Seite **Spalten Vergleiche** fest. Sie können die folgenden Einstellungen vornehmen.  
  
### <a name="use-during-test-comparisons"></a>Verwendung während der Test Vergleiche  
Bestimmen Sie, ob diese Spalte an der Überprüfung der Testergebnisse beteiligt ist.  
  
-   Wenn Sie **true**auswählen, vergleicht SSMA den Inhalt dieser Spalte nach dem Ausführen des Tests auf Sybase mit dem Inhalt der Spalte in SQL Server.
  
-   Wenn Sie **false**auswählen, wird die Spalte von der Ergebnis Überprüfung ausgeschlossen.  
  
### <a name="use-custom-scale"></a>Benutzerdefinierte Skalierung verwenden  
Für Spalten mit einem numerischen Datentyp können Sie eine benutzerdefinierte Skala für den Vergleich festlegen.  
  
-   Wenn Sie **true**auswählen, werden numerische Werte entsprechend dem **Vergleichs Skalierungs** Wert gerundet, bevor Sie verglichen werden.  
  
-   Wenn Sie **false**auswählen, ist der numerische Vergleich genau.  
  
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
Sie können die von SSMA Tester generierten SELECT-Anweisungen auf der Seite **SQL vergleichen** anzeigen. Der Tester vergleicht die Resultsets dieser Anweisungen zeilenweise. Jede nächste Zeile eines Sybase-Resultsets sollte gleich der nächsten Zeile des Resultsets sein, das in erstellt wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Sie können diese SELECT-Anweisungen bearbeiten, um eine benutzerdefinierte Überprüfung bereitzustellen Um die Änderungen in Sybase-und in-Anweisungen zu speichern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verwenden Sie die **Apply** -Schaltflächen unter dem Quell-und Ziel-SQL entsprechend.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anpassen von Aufruf Reihenfolge &#40;sybasedesql&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Test Fällen &#40;sybaseto SQL-&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
