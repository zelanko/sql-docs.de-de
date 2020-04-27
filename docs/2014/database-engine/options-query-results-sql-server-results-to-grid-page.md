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
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: b67926706674abb116b4f3075089853e6fbb665e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089308"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>Optionen (Abfrageergebnisse-SQL Server-auf Raster Seite Ergebnisse)
  Mithilfe dieser Seite können Sie die Anzeigeoptionen für Abfrageresultsets angeben, die im Rasterformat ausgegeben werden. Die an diesen Optionen vorgenommenen Änderungen werden nur für neue Abfragen in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet. Um die Optionen für die aktuellen Abfragen zu ändern, klicken Sie im Menü **Abfrage** auf **Abfrage Optionen** , oder klicken Sie mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] der rechten Maustaste in das Abfragefenster, und wählen Sie **Abfrage Optionen**aus. Klicken Sie im linken Bereich des Dialogfelds **Abfrageoptionen** unter **Ergebnisse**auf **Raster**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
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
  
  
