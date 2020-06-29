---
title: Hinzufügen eines Protokolls für Datenfluss-Leistungsindikatoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0076d61c4ad8abe3ef8ada818ac00a95b7bbe7c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439747"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsindikatoren](performance/performance-counters.md)   
 [Anzeigen der Protokolleinträge im Fenster „Protokollereignisse“](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)  
  
  
