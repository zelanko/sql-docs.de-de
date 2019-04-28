---
title: Zeigen Sie Protokolleinträge im Ereignisfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e3f5e41c6e20abbdcf78759c078632543217617
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926242"
---
# <a name="view-log-entries-in-the-log-events-window"></a>Anzeigen der Protokolleinträge im Fenster „Protokollereignisse“
  In diesem Verfahren wird das Ausführen eines Pakets und das Anzeigen der geschriebenen Protokolleinträge beschrieben. Sie können die Protokolleinträge in Echtzeit anzeigen. Die im Fenster **Protokollereignisse** geschriebenen Protokolleinträge können auch kopiert und für die spätere Analyse gespeichert werden.  
  
 Dabei müssen die Protokolleinträge nicht in ein Protokoll geschrieben werden, um die Einträge in das Fenster **Protokollereignisse** zu schreiben.  
  
### <a name="to-view-log-entries"></a>So zeigen Sie Protokolleinträge an  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Menü **SSIS** auf **Protokollereignisse**. Sie können das Fenster **Protokollereignisse** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.LogEvents einer beliebigen Tastenkombination zuordnen.  
  
3.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Sobald die Laufzeit feststellt, dass das Protokoll für Ereignisse und benutzerdefinierte Meldungen aktiviert wurde, werden die Protokolleinträge für die Ereignisse und Meldungen in das Fenster **Protokollereignisse** geschrieben.  
  
4.  Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.  
  
     Die Protokolleinträge sind so lange im Fenster **Protokollereignisse** verfügbar, bis Sie das Paket erneut ausführen, ein anderes Paket ausführen oder [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]schließen.  
  
5.  Zeigen Sie die Protokolleinträge im Fenster **Protokollereignisse** an.  
  
6.  Klicken Sie optional auf die zu kopierenden Protokolleinträge, klicken Sie auf die rechte Maustaste, und klicken dann Sie auf **Kopieren**.  
  
7.  Doppelklicken Sie optional auf einen Protokolleintrag, und zeigen Sie die Details eines einzelnen Protokolleintrags im Dialogfeld **Protokolleintrag** an.  
  
8.  Klicken Sie im Dialogfeld **Protokolleintrag** auf die Nach-Oben- oder Nach-Unten-Taste, um den vorigen oder nächsten Protokolleintrag anzuzeigen, und klicken Sie zum Kopieren des Protokolleintrags auf das Kopiersymbol.  
  
9. Öffnen Sie einen Texteditor, um den Protokolleintrag in eine Textdatei einzufügen und zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
