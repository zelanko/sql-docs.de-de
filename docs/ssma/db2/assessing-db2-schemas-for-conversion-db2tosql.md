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
ms.openlocfilehash: 506b9a32b465c9006fe4030bd6fcbb8ba4d0f136
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938336"
---
# <a name="assessing-db2-schemas-for-conversion-db2tosql"></a>Bewerten von DB2-Schemas für die Konvertierung (DB2ToSQL)
Vor dem Laden von Objekten und dem Migrieren von Daten zu müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sie bestimmen, wie komplex die Migration ist und wie viel Zeit die Migration dauern wird. SSMA kann einen Bewertungsbericht erstellen, in dem der Prozentsatz der Objekte angezeigt wird, die erfolgreich konvertiert werden. Mit SSMA können Sie auch die spezifischen Probleme anzeigen, die Konvertierungs Fehler verursachen.  
  
## <a name="creating-assessment-reports"></a>Erstellen von Bewertungsberichten  
Beim Erstellen dieses Bewertungsberichts konvertiert SSMA die ausgewählten DB2-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Syntax und zeigt dann die Ergebnisse an.  
  
**So erstellen Sie einen Bewertungsbericht**  
  
1.  Wählen Sie im DB2-metadatenexplorer die zu übertragenden Schemas aus.  
  
2.  Deaktivieren Sie die Kontrollkästchen neben den Kontrollkästchen, um einzelne Objekte auszulassen.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Schemas**, und wählen Sie dann **Bericht erstellen**aus.  
  
    Sie können einzelne Objekte auch analysieren, indem Sie mit der rechten Maustaste auf ein Objekt klicken und dann **Bericht erstellen**auswählen.  
  
    SSMA zeigt den Fortschritt in der Statusleiste am unteren Rand des Fensters an. Wenn der Ausgabebereich sichtbar ist, werden im Ausgabebereich auch Meldungen angezeigt.  
  
    Wenn die Bewertung fertiggestellt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das Fenster Migration Assistant für DB2: Bewertungsbericht angezeigt.  
  
## <a name="using-assessment-reports"></a>Verwenden von Bewertungsberichten  
Das Fenster "Bewertungsbericht" enthält drei Bereiche:  
  
-   Der linke Bereich enthält die Hierarchie der Objekte, die im Bewertungsbericht enthalten sind. Sie können die Hierarchie durchsuchen und Objekte und Kategorien von Objekten auswählen, um Konvertierungsstatistiken und Code anzuzeigen.  
  
-   Der Inhalt des rechten Bereichs hängt von dem Element ab, das im linken Bereich ausgewählt ist.  
  
    Wenn eine Gruppe von Objekten ausgewählt ist, z. b. ein Schema oder wenn eine Tabelle ausgewählt ist, enthält der Rechte Bereich den Bereich Konvertierungs Statistik und den Bereich Objekte nach Kategorien. Im Bereich Konvertierungs Statistik werden die Konvertierungsstatistiken für die ausgewählten Objekte angezeigt. Der Bereich Objekte nach Kategorien zeigt die Konvertierungsstatistiken für das Objekt oder die Kategorien von Objekten an.  
  
    Wenn eine Funktion, ein Paket, eine Prozedur, eine Sequenz oder eine Sicht ausgewählt ist, enthält der Rechte Bereich Statistiken, Quellcode und Zielcode.  
  
    -   Im oberen Bereich werden die Gesamt Statistiken für das Objekt angezeigt. Möglicherweise müssen Sie die **Statistik** erweitern, um diese Informationen anzuzeigen.  
  
    -   Der Quellbereich zeigt den Quellcode des-Objekts, das im linken Bereich ausgewählt ist. Die markierten Bereiche zeigen problematischen Quellcode.  
  
    -   Der Zielbereich zeigt den konvertierten Code. Roter Text zeigt problematische Code und Fehlermeldungen an.  
  
-   Der untere Bereich zeigt Konvertierungs Meldungen nach Nachrichtennummer gruppiert an. Sie können auf **Fehler**, **Warnungen**oder **Informationen** klicken, um Kategorien von Nachrichten anzuzeigen und dann eine Gruppe von Nachrichten zu erweitern. Klicken Sie auf eine einzelne Nachricht, um das Objekt im linken Bereich auszuwählen, und zeigen Sie die Details im rechten Bereich an.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analysieren von Konvertierungs Problemen mithilfe des Bewertungsberichts  
Im Bereich Konvertierungs Statistik werden die Konvertierungsstatistiken angezeigt. Wenn der Prozentsatz für eine Kategorie weniger als 100 Prozent beträgt, sollten Sie bestimmen, warum die Konvertierung nicht erfolgreich war.  
  
**So zeigen Sie Konvertierungsprobleme an**  
  
1.  Erstellen Sie den Bewertungsbericht mithilfe der Anweisungen im vorherigen Verfahren.  
  
2.  Erweitern Sie im linken Bereich Schemas oder Ordner mit einem roten Fehler Symbol. Erweitern Sie Elemente, bis Sie ein einzelnes Element auswählen, für das die Konvertierung fehlgeschlagen ist.  
  
3.  Klicken Sie oben im Bereich Quelle auf **nächstes Problem**.  
  
    Der problematische Code wird hervorgehoben, ebenso wie der zugehörige Code im Ziel Navigationsbereich.  
  
4.  Überprüfen Sie alle Fehlermeldungen, und legen Sie dann fest, was Sie mit dem Objekt tun möchten, das das Konvertierungs Problem verursacht hat:  
  
    -   Aktualisieren Sie die DB2-Syntax in SSMA. Sie können die Syntax für Prozeduren, Funktionen, Trigger, Paketfunktionen und Paket Prozeduren aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im DB2-metadatenexplorer-Bereich aus, klicken Sie auf die Registerkarte **SQL** , und ändern Sie den SQL-Code. Wenn Sie vom Element Weg navigieren, werden Sie aufgefordert, die aktualisierte Syntax zu speichern. Sie können die gemeldeten Fehler für das Objekt auf der Registerkarte **Bericht** anzeigen.  
  
    -   In DB2 können Sie das DB2-Objekt ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. Deaktivieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im metadatenexplorer und im DB2-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Objekte in laden und Daten aus DB2 migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
[Das Umrechnen von DB2-Schemas &#40;DB2ToSQL-&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Datenbanken zu SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
