---
title: Bewerten von Oracle-Schemas für die Konvertierung (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Analyzing Conversion Problems
ms.assetid: 4de9bcf6-1346-4740-87f9-7f24a8226357
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: acf31c29b498562708c7cb049e89a0a7425fd31f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288460"
---
# <a name="assessing-oracle-schemas-for-conversion-oracletosql"></a>Bewerten von Oracle-Schemas für die Konvertierung (OracleToSQL)
Bevor Sie Objekte laden und Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie sollten bestimmen, wie viel Zeit und Komplexität die Migration werden wird die Migration dauert. SSMA kann ein Bewertungsbericht erstellen, die den Prozentsatz von Objekten, die erfolgreich konvertiert wird. SSMA können Sie außerdem die spezifischen Probleme anzeigen, die dazu führen, dass bei der Konvertierung auftreten.  
  
## <a name="creating-assessment-reports"></a>Erstellen Berichte zur Bewertung  
Beim Erstellen dieser Bewertungsbericht konvertiert SSMA der ausgewählten Oracle-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und klicken Sie dann die Ergebnisse werden angezeigt.  
  
**So erstellen Sie einen Assessment-Bericht**  
  
1.  Wählen Sie in Oracle-Metadaten-Explorer die Schemas aus, um zu bewerten.  
  
2.  Um einzelne Objekte zu unterdrücken, deaktivieren Sie die Kontrollkästchen neben den.  
  
3.  Mit der rechten Maustaste **Schemas**, und wählen Sie dann **Bericht erstellen**.  
  
    Sie können auch einzelne Objekte analysieren, indem Sie mit der rechten Maustaste ein Objekt, und wählen Sie dann **Bericht erstellen**.  
  
    SSMA-Fortschritt wird in der Statusleiste am unteren Rand des Fensters angezeigt. Wenn im Ausgabebereich angezeigt wird, werden auch Meldungen im Ausgabebereich angezeigt.  
  
    Wenn die Bewertung abgeschlossen ist, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Oracle: Fenster "Assessment" wird angezeigt.  
  
## <a name="using-assessment-reports"></a>Verwenden von Assessment-Berichten  
Das Fenster Bewertungsbericht enthält drei Bereiche:  
  
-   Der linke Bereich enthält die Hierarchie der Objekte, die in den Bewertungsbericht enthalten sind. Sie können die Hierarchie durchsuchen und Auswählen von Objekten und Kategorien von Objekten um Konvertierungsstatistiken und den Code anzuzeigen.  
  
-   Der Inhalt im rechten Bereich abhängig ist, für das Element, das im linken Bereich ausgewählt ist.  
  
    Wenn eine Gruppe von Objekten ausgewählt ist, ein Schema, oder wenn eine Tabelle ausgewählt ist, der rechte Bereich enthält eine Konvertierung Statistiken Bereich und eine Objekte vom Bereich "Kategorien". Im Bereich Konvertierungsstatistiken zeigt die Konvertierungsstatistiken für die ausgewählten Objekte. Die Objekte nach Bereich "Kategorien" zeigt die Konvertierungsstatistiken für das Objekt oder die Kategorien von Objekten.  
  
    Wenn eine Funktion, Paket, Prozedur, Sequenz oder Ansicht ausgewählt ist, enthält im rechte Bereich Statistiken, Quellcode und Code des ereignisdateiziels.  
  
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
  
4.  Überprüfen Sie alle Fehlermeldungen, und klicken Sie dann zu bestimmen Sie, was Sie möchten mit dem Objekt, das die Ursache des Konvertierungsproblems:  
  
    -   Aktualisieren Sie die Oracle-Syntax in SSMA. Sie können die Syntax für die Prozeduren, Funktionen, Trigger, Paketfunktionen und verpackten Prozeduren aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im Oracle-Metadaten-Explorer, klicken Sie auf die **SQL** Registerkarte, und ändern Sie den SQL-Code. Wenn Sie vom Element weg navigieren, werden Sie aufgefordert, um die aktualisierte Syntax zu speichern. Sie können die gemeldeten Fehler für das Objekt anzeigen, auf die **Bericht** Registerkarte.  
  
    -   In Oracle können Sie das Oracle-Objekt zum Entfernen oder Überarbeiten problematischen Code ändern. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle-Datenbank &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer und Oracle-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten aus Oracle.  
  
## <a name="next-step"></a>Nächster Schritt  
[Konvertieren von Oracle-Schemas &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
