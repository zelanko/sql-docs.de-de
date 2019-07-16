---
title: Bewerten von MySQL-Datenbanken für die Konvertierung (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment reports
ms.assetid: 2a56a003-3b0f-453a-963c-00c9e40933ec
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ae9210444311267569d5f240d40252d4fe024877
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139208"
---
# <a name="assessing-mysql-databases-for-conversion-mysqltosql"></a>Bewerten von MySQL-Datenbanken für die Konvertierung (MySqlToSql)
Bevor Sie Objekte laden und Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, sollten Sie bestimmen, wie komplex die Migration werden und wie viel Zeit die Migration dauert. SSMA kann ein Bewertungsbericht erstellen, die den Prozentsatz von Objekten, die erfolgreich konvertiert wird. SSMA können Sie außerdem die spezifischen Probleme anzeigen, die dazu führen, dass bei der Konvertierung auftreten.  
  
## <a name="creating-assessment-reports"></a>Erstellen Berichte zur Bewertung  
Beim Erstellen dieser Bewertungsbericht konvertiert SSMA die ausgewählten MySQL-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax, und klicken Sie dann die Ergebnisse werden angezeigt.  
  
**So erstellen Sie einen Assessment-Bericht**  
  
1.  Wählen Sie im MySQL-Metadaten-Explorer die Schemas aus, um zu bewerten.  
  
2.  Um einzelne Objekte zu unterdrücken, deaktivieren Sie die Kontrollkästchen neben den.  
  
3.  Mit der rechten Maustaste **Schemas**, und wählen Sie dann **Bericht erstellen**.  
  
    Mit der rechten Maustaste in ein Objekt, um einzelne Objekte zu analysieren. Wählen Sie dann **Bericht erstellen**.  
  
    SSMA-Fortschritt wird in der Statusleiste am unteren Rand des Fensters angezeigt. Wenn im Ausgabebereich angezeigt wird, werden auch Meldungen im Ausgabebereich angezeigt.  
  
    Wenn die Bewertung abgeschlossen ist, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für MySQL Bewertungsbericht-Fenster wird angezeigt.  
  
## <a name="using-assessment-reports"></a>Verwenden von Assessment-Berichten  
Das Fenster Bewertungsbericht enthält drei Bereiche:  
  
-   Der linke Bereich enthält die Hierarchie der Objekte, die in den Bewertungsbericht enthalten sind. Sie können die Hierarchie durchsuchen und Auswählen von Objekten und Kategorien von Objekten um Konvertierungsstatistiken und den Code anzuzeigen.  
  
-   Der Inhalt im rechten Bereich abhängig ist, auf das Element, das im linken Bereich ausgewählt ist.  
  
    Wenn eine Gruppe von Objekten, z. B. Schema ausgewählt ist, enthält im rechte Bereich eine Konvertierung Statistiken Bereich und Objekte, durch den Bereich "Kategorien". Im Bereich Konvertierungsstatistiken zeigt die Konvertierungsstatistiken für die ausgewählten Objekte. Die Objekte nach Bereich "Kategorien" zeigt die Konvertierungsstatistiken für das Objekt oder die Kategorien von Objekten.  
  
    Wenn die Funktion, Prozedur, Tabelle oder Ansicht ausgewählt ist, enthält im rechte Bereich Statistiken, Quellcode und Code des ereignisdateiziels.  
  
    -   Im obere Bereich zeigt die Gesamtstatistik für das Objekt. Möglicherweise müssen Sie erweitern **Statistiken** zum Anzeigen dieser Informationen.  
  
    -   Der Quellbereich zeigt den Quellcode des Objekts, das im linken Bereich ausgewählt ist. Die markierten Bereiche zeigen problematisch Quellcode.  
  
    -   Der Zielbereich zeigt den konvertierten Code an. Roter Text zeigt die problematische Code und Fehlermeldungen.  
  
-   Im unteren Bereich zeigt die Konvertierung Nachrichten, gruppiert nach der Meldungsnummer. Klicken Sie auf **Fehler**, **Warnungen**, oder **Informationen** zeigt Kategorien von Nachrichten, und erweitern dann eine Gruppe von Nachrichten. Klicken Sie auf eine einzelne Nachricht aus, wählen Sie im linken Bereich das Objekt und die Details im rechten Bereich angezeigt.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analysieren der Probleme bei der Konvertierung mit den Bewertungsbericht  
Im Bereich Konvertierungsstatistiken zeigt die Konvertierungsstatistiken. Wenn der Prozentsatz für eine beliebige Kategorie weniger als 100 Prozent liegt, sollten Sie ermitteln, warum die Konvertierung nicht erfolgreich war.  
  
**Probleme bei der Konvertierung anzeigen**  
  
1.  Erstellen Sie den Bewertungsbericht, mithilfe der Anweisungen im vorherigen Verfahren.  
  
2.  Erweitern Sie im linken Bereich Schemas oder Ordner mit einem roten Fehlersymbol aus. Erweitern Elemente aus, bis Sie ein einzelnes Element auswählen, die Fehler bei der Konvertierung fortgesetzt werden.  
  
3.  Klicken Sie am oberen Rand des Bereichs für die Quelle, die auf **nächsten Problem**.  
  
    Der problematische Code ist hervorgehoben, wie der zugehörige Code im Ziel-Navigationsbereich ist.  
  
4.  Überprüfen Sie alle Fehlermeldungen, und klicken Sie dann zu bestimmen Sie, was Sie möchten mit dem Objekt, das die Ursache des Konvertierungsproblems.  
  
-   Aktualisieren Sie die MySQL-Syntax in SSMA. Sie können die Syntax nur für Prozeduren und Funktionen aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im MySQL-Metadaten-Explorer, klicken Sie auf die **SQL** Registerkarte, und ändern Sie den SQL-Code. Wenn Sie vom Element weg navigieren, werden Sie aufgefordert, um die aktualisierte Syntax zu speichern. Sie können die gemeldeten Fehler für das Objekt anzeigen, auf die **Bericht** Registerkarte.  
  
-   In MySQL können Sie das MySQL-Objekt zum Entfernen oder Überarbeiten problematischen Code ändern. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer und MySQL-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure und Daten aus MySQL migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
[Konvertieren von MySQL-Datenbanken &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
