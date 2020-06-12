---
title: Durchsuchen von Daten (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4a20484a85b459dad58e5e6687a6cc34a093b130
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528356"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>Daten durchsuchen (SQL Server Data Mining-Add-Ins)
  ![Assistent zum Durchsuchen von Daten](media/dmc-explore.gif "Assistent zum Durchsuchen von Daten")  
  
 Der Assistent zum durch **Suchen von Daten** hilft Ihnen, den Typ und die Menge der Daten in der Datentabelle zu verstehen. Der Assistent stellt die Verteilung und Werte für die ausgewählten Spalten spaltenweise grafisch dar. Anschließend können Sie die Gruppierung der Daten versuchsweise ändern oder das Diagramm, in dem der Inhalt angezeigt wird, zur Überprüfung in eine Excel-Arbeitsmappe kopieren.  
  
 Wenn Ihre Daten fortlaufende numerische Daten enthalten, können Sie zwischen den folgenden beiden Ansichten wechseln:  
  
-   **Liniendiagramm.** Dieses Diagramm zeichnet die Datenwerte auf der X-Achse und die Anzahl der Fälle auf der y-Achse auf.  
  
-   **Balkendiagramm.** Im Balkendiagramm werden die Werte nach der Anzahl von Fällen für jeden Wert gruppiert.  
  
 Wenn der Assistent Gruppen in den Daten findet, verwendet er die tatsächliche Verteilung der Datenwerte. Folglich werden im Balkendiagramm die numerischen Werte nicht in den typischen Ganzzahlunterteilungen auf den Achsen gruppiert (z. B. Zehner- oder Hundertergruppen). Stattdessen können die im Balkendiagramm angezeigten Bereiche durch Zahlen wie 43521-55603 (für die Einkommensspalte) angezeigt werden.  
  
 Wenn Sie die Daten in anderen Bereichen gruppieren möchten, sollten Sie diese Unterteilung in Excel vornehmen, bevor Sie die Daten analysieren. Oder Sie [können die Daten mithilfe des Assistenten zum](relabel-sql-server-data-mining-add-ins.md) neubezeichnen neu bezeichnen.  
  
## <a name="using-the-explore-data-wizard"></a>Verwenden des Assistenten zum Durchsuchen von Daten  
  
1.  Klicken Sie im **Data Mining** -Menüband auf **Daten durchsuchen**.  
  
2.  Wählen Sie im Dialogfeld **Quelle auswählen** die Tabelle oder den Zellen Bereich aus, der die Daten enthält.  
  
3.  Wählen Sie im Dialogfeld **Spalte auswählen** die zu analysierende Spalte aus den im Bereich angezeigten Beispiel Daten aus.  
  
4.  Wählen Sie im Dialogfeld **Daten durchsuchen** die Diagrammtypen für die Anzeige der Datenverteilung aus.  
  
5.  Sie können optional auch neue Spalten zu den Daten hinzufügen, die Segmentierung der Daten ändern oder das Diagramm in Excel kopieren.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Wenn Sie den Assistenten zum durch **Suchen von Daten** verwenden möchten, müssen sich die Daten in einer Excel-Datentabelle befinden.   
  
## <a name="see-also"></a>Weitere Informationen  
 [Prüfliste der Vorbereitung für Data Mining](checklist-of-preparation-for-data-mining.md)  
  
  
