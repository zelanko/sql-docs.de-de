---
title: 'Vorgehensweise: Ausführen des Analyse-Assistenten des Upgrade Advisor | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
caps.latest.revision: 36
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29aeaa20d5fed63731c84872ffb193da4bcfce27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282566"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>Vorgehensweise: Ausführen des Analyse-Assistenten des Upgrade Advisors
  Der Analyse-Assistent des Upgrade Advisors wird über die Startseite des Upgrade Advisors gestartet. In diesem Thema wird beschrieben, wie Sie den Analyse-Assistenten des Upgrade Advisors ausführen.  
  
> [!IMPORTANT]  
>  Wenn Sie den Analyse-Assistenten des Upgrade Advisors ausführen, speichert Upgrade Advisor die Berichte im Standardberichtsordner. Der Berichts-Viewer zeigt jedoch nur die fünf zuletzt gespeicherten Berichte an. Der Standardspeicherort für die Berichte ist eigene\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>Der Upgrade Advisor-Analyse-Assistenten ausführen.  
  
1.  Klicken Sie auf der Startseite des Upgrade Advisors auf **starten Analyse-Assistenten**.  
  
2.  Auf der  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten** Seite, geben Sie den Namen des zu scannenden Servers die **Servernamen** ein, und klicken Sie dann auf **erkennen**. Verwenden Sie die folgenden Richtlinien für den Servernamen:  
  
    -   Um nicht gruppierte Instanzen zu scannen, geben Sie den Computernamen ein.  
  
    -   Um gruppierte Instanzen zu scannen, geben Sie den virtuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Namen ein.  
  
    -   Um nicht gruppierte Komponenten zu scannen, die auf einem Knoten eines Clusters installiert sind, geben Sie den Knotennamen ein.  
  
    > [!WARNING]  
    >  Verbindungen mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die nicht auf den Standardport für Client-Verbindungen (1433) festgelegt ist, werden vom Upgrade Advisor nicht unterstützt. Wenn Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herstellen möchten, die nicht den Standardport (1433) verwendet, erstellen Sie einen Alias mithilfe die IP-Adresse und des Ports. Weitere Informationen zum Konfigurieren von Clientprotokollen und Erstellen eines Alias für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen finden Sie unter [Konfigurieren von Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md).  
    >   
    >  Wenn Sie keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert, auf dem Computer, auf dem Sie den Upgrade Advisor ausführen, klicken Sie auf **starten**, und führen Sie dann `cliconfg`. Daraufhin wird die  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server-Clientkonfiguration** Dialogfeld. Verwenden der **Alias** Tab, um den Alias zu erstellen.  
  
3.  Überprüfen Sie die Liste der erkannten Komponenten, ändern Sie die Auswahl nach Bedarf, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Verbindungsparameter** Seite, wählen Sie die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollen überprüfen, wählen die Authentifizierungsmethode und, falls erforderlich, geben Sie Informationen zu Benutzername und Kennwort, und klicken Sie dann auf **Weiter**.  
  
     Der Name der Standardinstanz lautet MSSQLSERVER.  
  
5.  Geben Sie für ausgewählte Komponenten die angeforderten Informationen ein. Weitere Informationen über einzelne Dialogfelder finden Sie unter [Upgrade Advisor-Benutzeroberflächenreferenz](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
6.  Auf der **Einstellungen für Upgrade Advisor bestätigen** überprüfen Sie die Informationen, die Sie eingegeben haben. Sie können auswählen, **Senden von Berichten an [!INCLUDE[msCoName](../../includes/msconame-md.md)]**  Wenn Sie den Upgradebericht einreichen möchten. Sie können auch die Datenschutzrichtlinie überprüfen.  
  
7.  Klicken Sie auf **ausführen** zum Analysieren der Instanzstatus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
8.  Wenn die Analyse abgeschlossen ist, klicken Sie auf **Bericht starten** um die erkannten Aktualisierungsprobleme anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Starten des Upgrade Advisors](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Ausführen von Upgrade Advisor &#40;-Benutzeroberfläche&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
