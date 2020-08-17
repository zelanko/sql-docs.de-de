---
description: Bewerten von Oracle-Schemas für die Konvertierung (OracleToSQL)
title: Bewerten von Oracle-Schemas für die Konvertierung (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Analyzing Conversion Problems
ms.assetid: 4de9bcf6-1346-4740-87f9-7f24a8226357
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 641d97868dcd308dbe487d43b7eba84a8b772371
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88320736"
---
# <a name="assessing-oracle-schemas-for-conversion-oracletosql"></a>Bewerten von Oracle-Schemas für die Konvertierung (OracleToSQL)
Vor dem Laden von Objekten und dem Migrieren von Daten zu müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie bestimmen, wie komplex die Migration ist und wie viel Zeit die Migration dauern wird. SSMA kann einen Bewertungsbericht erstellen, in dem der Prozentsatz der Objekte angezeigt wird, die erfolgreich konvertiert werden. Mit SSMA können Sie auch die spezifischen Probleme anzeigen, die Konvertierungs Fehler verursachen.  
  
## <a name="creating-assessment-reports"></a>Erstellen von Bewertungsberichten  
Beim Erstellen dieses Bewertungsberichts konvertiert SSMA die ausgewählten Oracle-Datenbankobjekte in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Syntax und zeigt dann die Ergebnisse an.  
  
**So erstellen Sie einen Bewertungsbericht**  
  
1.  Wählen Sie im Oracle-metadatenexplorer die zu übertragenden Schemas aus.  
  
2.  Deaktivieren Sie die Kontrollkästchen neben den Kontrollkästchen, um einzelne Objekte auszulassen.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Schemas**, und wählen Sie dann **Bericht erstellen**aus.  
  
    Sie können einzelne Objekte auch analysieren, indem Sie mit der rechten Maustaste auf ein Objekt klicken und dann **Bericht erstellen**auswählen.  
  
    SSMA zeigt den Fortschritt in der Statusleiste am unteren Rand des Fensters an. Wenn der Ausgabebereich sichtbar ist, werden im Ausgabebereich auch Meldungen angezeigt.  
  
    Wenn die Bewertung fertiggestellt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das Fenster Migration Assistant für Oracle: Assessment Report angezeigt.  
  
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
  
    -   Aktualisieren Sie die Oracle-Syntax in SSMA. Sie können die Syntax für Prozeduren, Funktionen, Trigger, Paketfunktionen und Paket Prozeduren aktualisieren. Um die Syntax zu aktualisieren, wählen Sie das Objekt im Bereich Oracle Metadata Explorer aus, klicken Sie auf die Registerkarte **SQL** , und ändern Sie dann den SQL-Code. Wenn Sie vom Element Weg navigieren, werden Sie aufgefordert, die aktualisierte Syntax zu speichern. Sie können die gemeldeten Fehler für das Objekt auf der Registerkarte **Bericht** anzeigen.  
  
    -   In Oracle können Sie das Oracle-Objekt ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle Database &#40;oracleto SQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
    -   Sie können das Objekt von der Migration ausschließen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Deaktivieren Sie im metadatenexplorer und im Oracle-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie die Objekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten aus Oracle migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
[Die Umstellung von Oracle-Schemas &#40;oracleto SQL-&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
