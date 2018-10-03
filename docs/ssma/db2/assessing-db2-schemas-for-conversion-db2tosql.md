---
title: Bewerten von DB2-Schemas für die Konvertierung (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8892f5a4-72ba-4406-8649-7a9d67f4c1d9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fe66ff5b8902a737ff9a2ac0815069a4f01ea129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608937"
---
# <a name="assessing-db2-schemas-for-conversion-db2tosql"></a>Bewerten von DB2-Schemas für die Konvertierung (DB2ToSQL)
Bevor Sie Objekte laden und Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie sollten bestimmen, wie viel Zeit und Komplexität die Migration werden wird die Migration dauert. SSMA kann ein Bewertungsbericht erstellen, die den Prozentsatz von Objekten, die erfolgreich konvertiert wird. SSMA können Sie außerdem die spezifischen Probleme anzeigen, die dazu führen, dass bei der Konvertierung auftreten.  
  
## <a name="creating-assessment-reports"></a>Erstellen Berichte zur Bewertung  
Beim Erstellen dieser Bewertungsbericht konvertiert SSMA der ausgewählten DB2-Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und klicken Sie dann die Ergebnisse werden angezeigt.  
  
**So erstellen Sie einen Assessment-Bericht**  
  
1.  Wählen Sie in DB2-Metadaten-Explorer die Schemas aus, um zu bewerten.  
  
2.  Um einzelne Objekte zu unterdrücken, deaktivieren Sie die Kontrollkästchen neben den.  
  
3.  Mit der rechten Maustaste **Schemas**, und wählen Sie dann **Bericht erstellen**.  
  
    Sie können auch einzelne Objekte analysieren, indem Sie mit der rechten Maustaste ein Objekt, und wählen Sie dann **Bericht erstellen**.  
  
    SSMA-Fortschritt wird in der Statusleiste am unteren Rand des Fensters angezeigt. Wenn im Ausgabebereich angezeigt wird, werden auch Meldungen im Ausgabebereich angezeigt.  
  
    Wenn die Bewertung abgeschlossen ist, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2: Bewertungsbericht-Fenster wird angezeigt.  
  
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
  
    -   Aktualisieren Sie die DB2-Syntax in SSMA. Sie können die Syntax für die Prozeduren, Funktionen, Trigger, Paketfunktionen und verpackten Prozeduren aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im DB2-Metadaten-Explorer, klicken Sie auf die **SQL** Registerkarte, und ändern Sie den SQL-Code. Wenn Sie vom Element weg navigieren, werden Sie aufgefordert, um die aktualisierte Syntax zu speichern. Sie können die gemeldeten Fehler für das Objekt anzeigen, auf die **Bericht** Registerkarte.  
  
    -   In DB2 können Sie ändern das DB2-Objekt zum Entfernen oder die problematischen Code zu überarbeiten. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer und DB2-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten aus DB2.  
  
## <a name="next-step"></a>Nächster Schritt  
[Konvertieren von DB2 Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
