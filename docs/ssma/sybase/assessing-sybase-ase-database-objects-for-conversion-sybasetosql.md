---
title: Bewerten die SAP ASE für die Konvertierung (SybaseToSQL Datenbankobjekte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c65c19ee3b95303afb0e1ae0a950efe548c8f0af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083533"
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>Bewerten von SAP ASE-Datenbankobjekten für die Konvertierung (SybaseToSQL)
Bevor Sie Objekte laden und Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL, Sie sollten bestimmen, wie die Komplexität der Migration und wie lange dauert. SSMA kann ein Bewertungsbericht enthält, die zeigt den Prozentsatz der Objekte und Prozeduren, die erfolgreich konvertiert werden, erstellen Sie [!INCLUDE[tsql](../../includes/tsql-md.md)]. SSMA können Sie außerdem die spezifischen Probleme anzeigen, die zu Konvertierungsfehlern führen können.  
  
## <a name="create-assessment-reports"></a>Erstellen Sie Berichte zur Bewertung  
Beim Erstellen dieses Bewertungsberichts konvertiert SSMA der ausgewählten SAP Adaptive Server Enterprise (ASE) Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Syntax, und klicken Sie dann die Ergebnisse werden angezeigt.  
  
**So erstellen Sie einen Assessment-Bericht**  
  
1.  Wählen Sie in der Sybase-Metadaten-Explorer Datenbanken, die Sie bewerten möchten.  
  
2.  Um einzelne Objekte zu unterdrücken, deaktivieren Sie die Kontrollkästchen neben den Objekten, die Sie nicht, um zu bewerten möchten.  
  
3.  Mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **Bericht erstellen**.  
  
    Sie können auch einzelne Objekte analysieren, indem Sie mit der rechten Maustaste ein Objekt, und wählen Sie dann **Bericht erstellen**.  
  
    SSMA zeigt den Fortschritt in der Statusleiste am unteren Rand des Fensters. Wenn im Ausgabebereich angezeigt wird, sehen Sie auch alle zugehörigen Nachrichten.  
  
    Wenn die Bewertung abgeschlossen ist, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Sybase: Fenster "Assessment" wird angezeigt.  
  
## <a name="use-assessment-reports"></a>Verwenden Sie die Berichte zur Bewertung  
Das Fenster Bewertungsbericht enthält drei Bereiche:  
  
-   Der linke Bereich enthält die Hierarchie der Objekte, die in den Bewertungsbericht enthalten sind. Sie können die Hierarchie durchsuchen und Auswählen von Objekten und Objektkategorien Konvertierungsstatistiken "und" Code anzeigen.  
  
-   Der Inhalt im rechten Bereich variiert basierend auf welches Element im linken Bereich ausgewählt wird.  
  
    Wenn eine Gruppe von Objekten (z. B. ein Schema) oder eine Tabelle ausgewählt ist, werden zwei Bereiche von im rechte Bereich angezeigt. Die **Konvertierungsstatistiken** Bereich zeigt die Konvertierungsstatistiken für die ausgewählten Objekte. Die **Objekte nach Kategorien** Bereich zeigt die Konvertierungsstatistiken für das Objekt oder die Kategorien von Objekten.  
  
    Wenn eine gespeicherte Prozedur, Sicht oder Trigger ausgewählt ist, enthält im rechte Bereich Statistiken, Quellcode und Code des ereignisdateiziels.  
  
    -   Im obere Bereich zeigt die Gesamtstatistik für das Objekt. Möglicherweise müssen Sie erweitern **Statistiken** zum Anzeigen dieser Informationen. 
    -   Der Quellbereich zeigt den Quellcode des Objekts, das im linken Bereich ausgewählt ist. Die markierten Bereiche zeigen problematisch Quellcode.  
    -   Der Zielbereich zeigt den konvertierten Code an. Roter Text zeigt die problematische Code und Fehlermeldungen.  
  
-   Im unteren Bereich zeigt die Konvertierung Nachrichten, gruppiert nach der Meldungsnummer. Wählen Sie **Fehler**, **Warnungen**, oder **Informationen** zeigt Kategorien von Nachrichten, und erweitern dann eine Gruppe von Nachrichten. Klicken Sie auf eine einzelne Nachricht auf das Objekt im linken Bereich, und klicken Sie dann anzeigen auswählen die Details im rechten Bereich aus.  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>Analysieren Sie Probleme bei der Konvertierung mithilfe des Bewertungsberichts  
Die **Konvertierungsstatistiken Bereiche** zeigen die Statistik für die Konvertierung. Wenn der Prozentsatz für eine beliebige Kategorie weniger als 100 Prozent liegt, sollten Sie ermitteln, warum die Konvertierung nicht erfolgreich war.  
  
**Probleme bei der Konvertierung anzeigen**  
  
1.  Erstellen Sie den Bewertungsbericht, mithilfe der Anweisungen im vorherigen Verfahren.  
  
2.  Erweitern Sie im linken Bereich Schemas oder Ordner mit einem roten Fehlersymbol aus. Erweitern Elemente aus, bis Sie ein einzelnes Element auswählen, die Fehler bei der Konvertierung fortgesetzt werden.  
  
3.  Wählen Sie am oberen Rand des Bereichs für die Quelle, **nächsten Problem**.  
    Der problematische Code markiert ist, wie der zugehörige in Code die **Ziel Navigation** Bereich.  
  
4.  Überprüfen Sie alle Fehlermeldungen, und klicken Sie dann zu bestimmen Sie, was Sie möchten mit dem Objekt, das die Ursache des Konvertierungsproblems:  
  
    -   Aktualisieren Sie die ASE-Syntax in SSMA. Sie können die Syntax nur für gespeicherte Prozeduren und Trigger aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt in der Sybase-Metadaten-Explorer-Bereich, klicken Sie auf die **SQL** Registerkarte, und klicken Sie dann den SQL-Code bearbeiten. Wenn Sie vom Element weg navigieren, werden Sie aufgefordert, um die aktualisierte Syntax zu speichern. Zeigen Sie die gemeldeten Fehler für das Objekt, auf die **Bericht** Registerkarte.  
  
    -   In App Service-Umgebung können Sie das ASE-Objekt zum Entfernen oder Überarbeiten problematischen Code ändern. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Metadaten-Explorer und Sybase-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL und Migrieren von Daten aus der ASE.
  
## <a name="next-steps"></a>Nächste Schritte  
[Konvertieren von SAP ASE-Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von SAP ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
