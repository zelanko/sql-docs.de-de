---
title: Bewerten von SAP ASE-Datenbankobjekten für die Konvertierung (sybasetoisql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: fba4692780b9f9f2c556634bf1676bc00bbba169
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932611"
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>Bewerten von SAP ASE-Datenbankobjekten für die Konvertierung (sybasetoisql)
Vor dem Laden von Objekten und der Migration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Daten zu oder Azure SQL sollten Sie bestimmen, wie komplex die Migration und wie viel Zeit Sie dauern sollte. SSMA kann einen Bewertungsbericht erstellen, der den Prozentsatz der Objekte und Prozeduren anzeigt, die erfolgreich in konvertiert werden [!INCLUDE[tsql](../../includes/tsql-md.md)] . Mit SSMA können Sie auch die spezifischen Probleme anzeigen, die Konvertierungs Fehler verursachen können.  
  
## <a name="create-assessment-reports"></a>Bewertungsberichte erstellen  
Beim Erstellen dieses Bewertungsberichts konvertiert SSMA die ausgewählten SAP Adaptive Server Enterprise (ASE)-Datenbankobjekte in die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Syntax und zeigt dann die Ergebnisse an.  
  
**So erstellen Sie einen Bewertungsbericht**  
  
1.  Wählen Sie im Sybase-metadatenexplorer die Datenbanken aus, die Sie bewerten möchten.  
  
2.  Wenn Sie einzelne Objekte weglassen möchten, deaktivieren Sie die Kontrollkästchen neben den Objekten, die nicht bewertet werden sollen.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Datenbanken**und dann auf **Bericht erstellen**.  
  
    Sie können einzelne Objekte auch analysieren, indem Sie mit der rechten Maustaste auf ein Objekt klicken und dann **Bericht erstellen**auswählen.  
  
    SSMA zeigt den Fortschritt in der Statusleiste am unteren Rand des Fensters an. Wenn der Ausgabebereich sichtbar ist, werden auch zugehörige Meldungen angezeigt.  
  
    Wenn die Bewertung fertiggestellt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das Fenster Migration Assistant für Sybase: Bewertungsbericht angezeigt.  
  
## <a name="use-assessment-reports"></a>Verwenden von Bewertungsberichten  
Das Fenster "Bewertungsbericht" enthält drei Bereiche:  
  
-   Der linke Bereich enthält die Hierarchie der Objekte, die im Bewertungsbericht enthalten sind. Sie können die Hierarchie durchsuchen und Objekte und Objektkategorien auswählen, um Konvertierungsstatistiken und Code anzuzeigen.  
  
-   Der Inhalt des rechten Bereichs variiert je nach ausgewähltem Element im linken Bereich.  
  
    Wenn eine Gruppe von Objekten (z. b. ein Schema) oder eine Tabelle ausgewählt ist, werden im rechten Bereich zwei Bereiche angezeigt. Im Bereich **Konvertierungs Statistik** werden die Konvertierungsstatistiken für die ausgewählten Objekte angezeigt. Der Bereich **Objekte nach Kategorien** zeigt die Konvertierungsstatistiken für das Objekt oder die Kategorien von Objekten an.  
  
    Wenn eine gespeicherte Prozedur, eine Sicht oder ein Auslösung ausgewählt ist, enthält der Rechte Bereich Statistiken, Quellcode und Zielcode.  
  
    -   Im oberen Bereich werden die Gesamt Statistiken für das Objekt angezeigt. Möglicherweise müssen Sie die **Statistik** erweitern, um diese Informationen anzuzeigen. 
    -   Der Quellbereich zeigt den Quellcode des-Objekts, das im linken Bereich ausgewählt ist. Die markierten Bereiche zeigen problematischen Quellcode.  
    -   Der Zielbereich zeigt den konvertierten Code. Roter Text zeigt problematische Code und Fehlermeldungen an.  
  
-   Der untere Bereich zeigt Konvertierungs Meldungen nach Nachrichtennummer gruppiert an. Wählen Sie **Fehler**, **Warnungen**oder **Informationen** aus, um Kategorien von Nachrichten anzuzeigen, und erweitern Sie dann eine Gruppe von Nachrichten. Klicken Sie auf eine einzelne Nachricht, um das Objekt im linken Bereich auszuwählen, und zeigen Sie dann die Details im rechten Bereich an.  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>Analysieren von Konvertierungs Problemen mithilfe des Bewertungsberichts  
Im Bereich **Konvertierungs Statistik** werden die Konvertierungsstatistiken angezeigt. Wenn der Prozentsatz für eine Kategorie weniger als 100 Prozent beträgt, sollten Sie bestimmen, warum die Konvertierung nicht erfolgreich war.  
  
**So zeigen Sie Konvertierungsprobleme an**  
  
1.  Erstellen Sie den Bewertungsbericht mithilfe der Anweisungen im vorherigen Verfahren.  
  
2.  Erweitern Sie im linken Bereich Schemas oder Ordner mit einem roten Fehler Symbol. Erweitern Sie Elemente, bis Sie ein einzelnes Element auswählen, für das die Konvertierung fehlgeschlagen ist.  
  
3.  Wählen Sie oben im Bereich Quelle die Option **nächstes Problem**aus.  
    Der problematische Code wird hervorgehoben, ebenso wie der zugehörige Code im **Ziel Navigations** Bereich.  
  
4.  Überprüfen Sie alle Fehlermeldungen, und legen Sie dann fest, was Sie mit dem Objekt tun möchten, das das Konvertierungs Problem verursacht hat:  
  
    -   Aktualisieren Sie die ASE-Syntax in SSMA. Sie können die Syntax nur für gespeicherte Prozeduren und Trigger aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im Sybase-metadatenexplorer-Bereich aus, klicken Sie auf die Registerkarte **SQL** , und bearbeiten Sie dann den SQL-Code. Wenn Sie vom Element Weg navigieren, werden Sie aufgefordert, die aktualisierte Syntax zu speichern. Zeigen Sie die gemeldeten Fehler für das Objekt auf der Registerkarte **Bericht** an.  
  
    -   In ASE können Sie das ASE-Objekt ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der Sybase-ASE &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Deaktivieren Sie in oder im Azure SQL-metadatenexplorer und im Sybase-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL laden und Daten aus ASE migrieren.
  
## <a name="next-steps"></a>Nächste Schritte  
[Umstellen von SAP ASE-Datenbankobjekten &#40;sybaseumsql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von SAP ASE-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
