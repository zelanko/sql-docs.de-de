---
title: 'Vorgehensweise: Anzeigen eine Berichts des Upgrade Advisors | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b3617edd1d79e258490c0cc44fc3b21e012c4573
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057527"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>Vorgehensweise: Anzeigen eines Berichts des Upgrade Advisors
  Der Upgrade Advisor erstellt Berichte für alle Komponenten, die Sie zur Analyse auswählen. In diesem Thema wird beschrieben, wie Sie einen Bericht des Upgrade Advisors über die Startseite des Upgrade Advisors anzeigen.  
  
> [!IMPORTANT]  
>  Der Berichts-Viewer lädt Dateien auf der Grundlage von Standarddateinamen. Wenn die Dateien umbenannt wurden, werden sie vom Berichts-Viewer nicht geladen.  
  
### <a name="to-view-a-report"></a>So zeigen Sie einen Bericht an  
  
1.  Klicken Sie auf **starten**, klicken Sie auf **Programme**, klicken Sie auf **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, und klicken Sie dann auf  **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.  
  
2.  Klicken Sie auf der Startseite des Upgrade Advisors auf **Viewer des Upgrade Advisors Bericht starten**.  
  
3.  So wählen Sie am Standardspeicherort auf dem Computer einen Bericht aus:  
  
    1.  In der **Server** Liste, wählen Sie einen Server.  
  
    2.  In der **Instanz oder Komponente** wählen Sie eine Komponente oder Komponenteninstanz/Kombination.  
  
     So wählen Sie an einem anderen Speicherort einen Bericht aus:  
  
    1.  Klicken Sie auf die **geöffneten Bericht** Link.  
  
    2.  Navigieren Sie zum Speicherort des Berichts, und doppelklicken Sie dann auf die XML-Datei.  
  
     Der Upgrade Advisor speichert bis zu fünf Berichte früherer Analysen als Verlauf. Um diese Berichte anzuzeigen, klicken Sie auf die **Bericht** im Dropdown Listenfeld, und wählen Sie einen Bericht. Die Berichte werden nach dem Zeitstempel für ihren Generierungszeitpunkt aufgeführt.  
  
     Der Bericht enthält die folgenden Details für alle erkannten Probleme:  
  
    -   **Wichtigkeit**, die angibt, wie wichtig es ist, um das Problem zu beheben.  
  
    -   **Zeitpunkt der Behebung**, der angibt, ob Sie das Problem vor oder nach dem Upgrade auf Update sollte (oder müssen) [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vor oder nach der Migration der Anwendung oder die Daten oder jedes Mal, wenn.  
  
    -   Eine kurze Beschreibung des Problems.  
  
4.  Wenn der Bericht mehr als 20 Einträge enthält, klicken Sie auf den grünen Vorwärtspfeil am Anfang oder am Ende des Berichts, um die nächste Elementgruppe anzuzeigen. Klicken Sie auf die grüne Zurück-Schaltfläche, um die vorhergehenden 20 Elemente anzuzeigen.  
  
5.  Klicken Sie auf eine Spaltenüberschrift, um den Bericht zu sortieren.  
  
6.  Um Details für ein bestimmtes Element anzuzeigen, klicken Sie auf das gewünschte Element. Eine Beschreibung des Problems wird angezeigt, zusammen mit zusätzlichen Optionen:  
  
    -   Um die Objekte anzuzeigen, in denen dieses Problem gefunden wurde, klicken Sie auf **betroffene Objekte anzeigen**.  
  
    -   Klicken Sie zum Anzeigen der Hilfe für das Problem auf **Weitere Informationen zu diesem Problem und dessen problemlösung**.  
  
    -   Um das Problem als gelöst zu markieren, sodass es beim erneuten des Berichts anzeigen ausgeblendet, wählen Sie **dieses Problem wurde behoben**.  
  
> [!NOTE]  
>  Der Bericht enthält möglicherweise ein Element für nicht zu erkennende Probleme. Dies sind Probleme, die nicht erkannt werden können oder zu viele falsche positive Ergebnisse generieren würden. Klicken Sie auf die **Weitere Informationen zu diesem Problem und dessen problemlösung** Link, um eine Liste der nicht erkennbaren Probleme für die Komponente anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Vorgehensweise: Ausführen des Analyse-Assistenten des Upgrade Advisor](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Upgrade Advisor: Themen zur Vorgehensweise](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  