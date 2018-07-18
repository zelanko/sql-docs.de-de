---
title: Abfrageoptionen, Ergebnisse (Seite "Text") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: d6c4fb6fe50f20bcac8d4f16644a35466a7b2f2e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205750"
---
# <a name="query-options-results-text-page"></a>Abfrageoptionen, Ergebnisse (Seite Text)
  Mithilfe dieser Seite können Sie die Optionen für die Anzeige eines Abfrageresultsets im Textformat angeben. Die Einstellungen auf dieser Seite gelten auch dann, wenn **Ergebnisse in Datei** ausgewählt wurde.  
  
 **Ausgabeformat**  
 Standardmäßig werden die Ausgaben in Spalten angezeigt, die durch Auffüllen der Ergebnisse mit Leerstellen erstellt werden. Als weitere Optionen können Kommas, Tabstopps oder Leerzeichen zur Trennung der Spalten gewählt werden. Aktivieren Sie das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** , um im Feld **Benutzerdefiniertes Trennzeichen** ein anderes Trennzeichen festzulegen.  
  
 **Benutzerdefiniertes Trennzeichen**  
 Geben Sie das gewünschte Zeichen zum Trennen der Spalten an. Diese Option ist nur verfügbar, wenn im Feld **Ausgabeformat** das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** aktiviert wurde.  
  
 **Spaltenheader im Resultset einschließen**  
 Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nicht möchten, dass jede Spalte mit einem Spaltentitel versehen wird.  
  
 **Bildlauf beim Empfangen von Ergebnissen**  
 Aktivieren Sie dieses Kontrollkästchen, wenn zuerst die zuletzt zurückgegebenen Datensätze am unteren Ende der Ergebnisliste angezeigt werden sollen. Deaktivieren Sie dieses Kontrollkästchen, wenn zunächst die ersten empfangenen Zeilen angezeigt werden sollen.  
  
 **Numerische Werte rechts ausrichten**  
 Aktivieren Sie dieses Kontrollkästchen, um numerische Werte an der Spalte rechts auszurichten. Das kann die Überprüfung von Zahlen mit einer festen Anzahl von Dezimalstellen erleichtern.  
  
 **Verwerfen von Ergebnis nach der abfrageausführung**  
 Gibt Arbeitsspeicher frei, indem die Abfrageergebnisse nach der Anzeige auf dem Bildschirm verworfen werden.  
  
 **Ergebnisse auf separater Registerkarte anzeigen**  
 Aktivieren Sie dieses Kontrollkästchen, um das Resultset in einem neuen Dokumentfenster anzuzeigen statt im unteren Bereich des Dokumentfensters der Abfrage.  
  
 **Wechseln Sie zur Registerkarte "Ergebnisse" nach Ausführung der Abfrage**  
 Aktivieren Sie dieses Kontrollkästchen, wenn der Fokus automatisch auf das Resultset verschoben werden soll.  
  
 **Maximale Anzahl von Zeichen pro Spalte angezeigte**  
 Dieser Wert liegt standardmäßig bei 256. Erhöhen Sie diesen Wert, wenn Sie größere Resultsets ohne Kürzungen anzeigen möchten.  
  
 **Auf Standard zurücksetzen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
## <a name="saving-a-text-result-set-with-headers"></a>Speichern eines Resultsets als Text mit Header  
 Um Abfrageergebnisse als Textdatei mit Header zu speichern, aktivieren Sie das Kontrollkästchen **Spaltenheader im Resultset einschließen** , und wählen Sie ein getrenntes Ausgabeformat aus. Jetzt enthält die Berichtsdatei Header, wenn Sie auf der Symbolleiste auf **Ergebnisse in Datei** klicken, oder wenn Sie mit der rechten Maustaste auf Abfrageergebnisse klicken, dann auf **Ergebnisse speichern unter**klicken, einen Dateinamen eingeben und dann auf **Speichern**klicken.  
  
  
