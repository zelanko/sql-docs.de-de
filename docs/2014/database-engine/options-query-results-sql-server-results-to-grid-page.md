---
title: Optionen (Abfrageergebnisse-SQL Server-auf Raster Seite Ergebnisse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9bde39c64fdf2fbabaec85772d4bfa44d86fd1da
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83856640"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>Optionen (Abfrageergebnisse-SQL Server-auf Raster Seite Ergebnisse)
  Mithilfe dieser Seite können Sie die Anzeigeoptionen für Abfrageresultsets angeben, die im Rasterformat ausgegeben werden. Die an diesen Optionen vorgenommenen Änderungen werden nur für neue Abfragen in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet. Um die Optionen für die aktuellen Abfragen zu ändern, klicken Sie im Menü **Abfrage** auf **Abfrage Optionen** , oder klicken Sie mit der rechten Maustaste in das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Abfragefenster, und wählen Sie **Abfrage Optionen**aus. Klicken Sie im linken Bereich des Dialogfelds **Abfrageoptionen** unter **Ergebnisse**auf **Raster**.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Abfrage in das Resultset einschließen**  
 Gibt den Text der Abfrage als Teil der Abfrageausgabe zurück.  
  
 **Spaltenheader beim Kopieren oder Speichern der Ergebnisse einschließen**  
 Aktivieren Sie dieses Kontrollkästchen, um Spaltenheader beim Kopieren von Ergebnissen in die Zwischenablage oder beim Speichern in einer Datei einzuschließen. Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nur die Ergebnisdaten und nicht die Spaltenheader speichern oder kopieren möchten.  
  
 **Ergebnisse nach der Ausführung verwerfen**  
 Verhindert, dass Abfrageergebnisse im Überprüfungsbereich angezeigt werden. Die Ergebnisse werden unmittelbar nach der Ausführung verworfen. Durch Aktivieren dieser Option können Sie Speicherplatz einsparen.  
  
 **Ergebnisse auf separater Registerkarte anzeigen**  
 Aktivieren Sie dieses Kontrollkästchen, wenn das Resultset nicht im unteren Bereich des Dokumentfensters der Abfrage, sondern in einer neuen Registerkarte angezeigt werden soll.  
  
 **Nach Ausführung der Abfrage zur Ergebnisregisterkarte wechseln**  
 Wählen Sie diese Option, um nach der Ausführung einer Abfrage mit der Anzeige automatisch zum Ergebnisbereich zu wechseln.  
  
 **Maximale Anzahl von abgerufenen Zeichen**  
 **Nicht-XML-Daten**:  
  
 Geben Sie eine Zahl zwischen 1 und 65.535 ein, um die maximale Anzahl der in einer Zelle angezeigten Zeichen anzugeben.  
  
> [!NOTE]  
>  Wenn Sie eine große Anzahl von Zeichen angeben, werden die Daten im Resultset unter Umständen abgeschnitten angezeigt. Die maximale Anzahl der pro Zelle angezeigten Zeichen ist von der Schriftgröße abhängig. Wenn große Resultsets zurückgegeben werden, kann ein großer Wert in diesem Feld dazu führen, dass [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] viel Arbeitsspeicher beansprucht und die Systemleistung beeinträchtigt.  
  
 **XML-Daten**:  
  
 Wählen Sie **1 MB**, **2 MB**oder **5 MB**aus. Wählen Sie **Unbegrenzt** aus, um alle Zeichen abzurufen.  
  
 **Standard wiederherstellen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
