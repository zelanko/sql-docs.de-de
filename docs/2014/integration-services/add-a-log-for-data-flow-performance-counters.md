---
title: Hinzufügen eines Protokolls für Datenfluss-Leistungsindikatoren | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e659cfb46c514a13e090e244ee56c4bbc7ce8e61
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149102"
---
# <a name="add-a-log-for-data-flow-performance-counters"></a>Hinzufügen eines Protokolls für Datenfluss-Leistungsindikatoren
  In diesem Verfahren wird beschrieben, wie ein Protokoll für die von der Datenfluss-Engine bereitgestellten Leistungsindikatoren hinzugefügt wird.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auf einem Computer installieren, auf dem [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]ausgeführt wird, und anschließend ein Upgrade des betreffenden Computers auf [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)]ausführen, werden beim Upgradeprozess die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Leistungsindikatoren vom Computer entfernt. Zum Wiederherstellen der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Leistungsindikatoren auf dem Computer führen Sie Setup von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] im Reparaturmodus aus.  
  
### <a name="to-add-logging-of-performance-counters"></a>So fügen Sie die Protokollierung von Leistungsindikatoren hinzu  
  
1.  Wenn Sie die klassische Ansicht verwenden, klicken Sie in der **Systemsteuerung**auf **Verwaltung**. Wenn Sie die Kategorieansicht verwenden, klicken Sie auf **Leistung und Wartung** und dann auf **Verwaltung**.  
  
2.  Klicken Sie auf **Leistung**.  
  
3.  Erweitern Sie im Dialogfeld **Leistung** die Option **Leistungsdatenprotokolle und Warnungen**, klicken Sie mit der rechten Maustaste auf **Leistungsindikatorenprotokolle**, und klicken Sie dann auf **Neue Protokolleinstellungen**. Geben Sie den Namen des Protokolls ein. Geben Sie z. B. **MeinProtokoll**ein.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie im Dialogfeld **MeinProtokoll** auf **Indikatoren hinzufügen**.  
  
6.  Klicken Sie auf **Lokale Leistungsindikatoren verwenden** , um die Leistungsindikatoren auf dem lokalen Computer zu protokollieren. Oder klicken Sie auf **Leistungsindikatoren auswählen von:** , und wählen Sie dann einen Computer aus der Liste aus, um die Leistungsindikatoren auf dem angegebenen Computer zu protokollieren.  
  
7.  Wählen Sie im Dialogfeld **Indikatoren hinzufügen** die Option **SQLServer:SSIS-Pipeline** aus der Liste **Leistungsobjekt** aus.  
  
8.  Gehen Sie zur Auswahl von Leistungsindikatoren wie folgt vor:  
  
    -   Wählen Sie **Alle Indikatoren** , um alle Leistungsindikatoren zu protokollieren.  
  
    -   Wählen Sie **Indikatoren aus Liste auswählen** , und wählen Sie die zu verwendenden Leistungsindikatoren aus.  
  
9. Klicken Sie auf **Hinzufügen**.  
  
10. Klicken Sie auf **Schließen**.  
  
11. Prüfen Sie im Dialogfeld **MeinProtokoll** die Liste **Indikatoren** mit den protokollierten Leistungsindikatoren.  
  
12. Um weitere Indikatoren hinzuzufügen, wiederholen Sie die Schritte 5 bis 10.  
  
13. Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Sie müssen den Dienst Leistungsprotokolle und Warnungen mithilfe eines lokalen Kontos oder eines Domänenkontos starten, das Mitglied der Administratorengruppe ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Leistungsindikatoren](performance/performance-counters.md)   
 [Anzeigen der Protokolleinträge im Fenster „Protokollereignisse“](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)  
  
  