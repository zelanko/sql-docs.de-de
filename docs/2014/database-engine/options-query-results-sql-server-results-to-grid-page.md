---
title: Optionen (Abfrageergebnisse – SQL Server-Abfrageergebnisse Rasterseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 23e5634a67ff6daec4f6b0852905d8596b885c60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318900"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>Optionen (Abfrageergebnisse – SQL Server-Abfrageergebnisse auf der Seite)
  Mithilfe dieser Seite können Sie die Anzeigeoptionen für Abfrageresultsets angeben, die im Rasterformat ausgegeben werden. Die an diesen Optionen vorgenommenen Änderungen werden nur für neue Abfragen in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet. Wenn Sie diese Optionen für die aktuellen Abfragen ändern möchten, klicken Sie entweder im Menü **Abfrage** auf **Abfrageoptionen**, oder klicken Sie mit der rechten Maustaste in das Abfragefenster von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], und wählen Sie **Abfrageoptionen**. Klicken Sie im linken Bereich des Dialogfelds **Abfrageoptionen** unter **Ergebnisse**auf **Raster**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Abfrage in Resultset einschließen**  
 Gibt den Text der Abfrage als Teil der Abfrageausgabe zurück.  
  
 **Schließen Sie Spaltenheader beim Kopieren oder Speichern der Ergebnisse ein**  
 Aktivieren Sie dieses Kontrollkästchen, um Spaltenheader beim Kopieren von Ergebnissen in die Zwischenablage oder beim Speichern in einer Datei einzuschließen. Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nur die Ergebnisdaten und nicht die Spaltenheader speichern oder kopieren möchten.  
  
 **Ergebnisse nach der Ausführung verwerfen**  
 Verhindert, dass Abfrageergebnisse im Überprüfungsbereich angezeigt werden. Die Ergebnisse werden unmittelbar nach der Ausführung verworfen. Durch Aktivieren dieser Option können Sie Speicherplatz einsparen.  
  
 **Ergebnisse auf separater Registerkarte anzeigen**  
 Aktivieren Sie dieses Kontrollkästchen, wenn das Resultset nicht im unteren Bereich des Dokumentfensters der Abfrage, sondern in einer neuen Registerkarte angezeigt werden soll.  
  
 **Wechseln Sie zur Registerkarte "Ergebnisse" nach Ausführung der Abfrage**  
 Wählen Sie diese Option, um nach der Ausführung einer Abfrage mit der Anzeige automatisch zum Ergebnisbereich zu wechseln.  
  
 **Maximale Anzahl von abgerufenen Zeichen**  
 **Nicht-XML-Daten**:  
  
 Geben Sie eine Zahl zwischen 1 und 65.535 ein, um die maximale Anzahl der in einer Zelle angezeigten Zeichen anzugeben.  
  
> [!NOTE]  
>  Wenn Sie eine große Anzahl von Zeichen angeben, werden die Daten im Resultset unter Umständen abgeschnitten angezeigt. Die maximale Anzahl der pro Zelle angezeigten Zeichen ist von der Schriftgröße abhängig. Wenn große Resultsets zurückgegeben werden, kann ein großer Wert in diesem Feld dazu führen, dass [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] viel Arbeitsspeicher beansprucht und die Systemleistung beeinträchtigt.  
  
 **XML-Daten**:  
  
 Wählen Sie **1 MB**, **2 MB**oder **5 MB**aus. Wählen Sie **Unbegrenzt** aus, um alle Zeichen abzurufen.  
  
 **Auf Standard zurücksetzen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
