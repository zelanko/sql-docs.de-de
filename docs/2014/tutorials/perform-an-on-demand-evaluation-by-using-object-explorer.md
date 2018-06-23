---
title: Führen Sie eine bedarfsgesteuerte Auswertung mittels Objekt-Explorer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 55ca364c60c2b9fcca407561ed195035ce7205fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058204"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Ausführen einer bedarfsgesteuerten Auswertung mit dem Objekt-Explorer
  In dieser Aufgabe verwenden Sie den Objekt-Explorer, um eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien für [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] auf einer einzelnen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz auszuführen.  
  
> [!NOTE]  
>  Sie können Richtlinien auch mithilfe der registrierten Server auf einer einzelnen Instanz auswerten. Weitere Informationen finden Sie unter [Ausführen einer On-Demand-Auswertung von registrierte Server verwenden](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Diese Lektion basiert auf der von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ausgeführten Version von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Um eine bedarfsgesteuerte Auswertung von best Practices-Richtlinien gegen Instanzen auszuführen, die ausgeführt werden [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], müssen Sie das Verfahren in diesem Thema verwenden [Ausführen einer On-Demand-Auswertung von registrierte Server verwenden](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>So führen Sie eine bedarfsgesteuerte Auswertung mit dem Objekt-Explorer aus  
  
1.  Starten Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], und stellen Sie dann eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)] her.  
  
2.  Erweitern Sie im Objekt-Explorer **Management**, erweitern Sie **richtlinienverwaltung**, mit der rechten Maustaste **Richtlinien**, und klicken Sie dann auf **auswerten**.  
  
    > [!NOTE]  
    >  Standardmäßig wird die lokale Instanz als Quelle der Richtlinien verwendet. Wenn Sie zuvor Best Practices-Richtlinien importiert haben, werden diese zusammen mit anderen, von Ihnen erstellten Richtlinien aufgeführt. Sie können jede beliebige importierte besten Practices-Richtlinien auswählen, und klicken Sie dann auf **auswerten**. Falls Sie keine Best Practices-Richtlinien importiert haben, fahren Sie mit dieser Prozedur fort.  
  
3.  In der **Richtlinien auswerten** Dialogfeld neben der **Quelle** klicken Sie auf die Auslassungspunkte (**...** ) Schaltfläche.  
  
4.  In der **Quelle auswählen** (Dialogfeld), wählen Sie entweder **Dateien** oder **Server** als Quelle der auszuwertenden Richtliniendateien. Wenn Sie auf **Server**, führen Sie eine bedarfsgesteuerte Auswertung von besten Practices-Richtlinien, die zuvor in die Richtlinie der richtlinienbasierten Verwaltung auf einem lokalen oder remote-Server importiert wurden. In diesem Lernprogramm klicken Sie auf **Dateien**, und wählen Sie dann die einzelnen Richtliniendateien aus, die Sie auswerten möchten. Führen Sie hierzu folgende Schritte aus:  
  
    1.  Klicken Sie auf **Dateien**.  
  
    2.  Neben **Dateien**, klicken Sie auf die Auslassungspunkte (**...** ) Schaltfläche.  
  
    3.  In der **Richtlinie auswählen** (Dialogfeld), navigieren Sie zum folgenden Ordner, die besten Practices-Richtlinien enthält:  
  
         **C:\Programme\Microsoft Dateien (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Abhängig davon, wo die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Programmdateien installiert sind, ob ein 32-Bit- oder 64-Bit-Betriebssystem ausgeführt bzw. ein Sprachbezeichner verwendet wird, kann sich der Dateipfad ändern.  
  
    4.  Wählen Sie eine oder mehrere XML-Richtliniendateien ausgewertet, und klicken Sie auf **öffnen**.  
  
         Die Liste der ausgewählten Dateien wird angezeigt, der **Dateien** Feld.  
  
    5.  In der **Quelle auswählen** (Dialogfeld), klicken Sie auf **OK**.  
  
    6.  Wenn die **Richtlinien laden** Dialogfeld angezeigt wird, klicken Sie auf **schließen**.  
  
     Die Richtlinien, die Sie ausgewählt haben, werden auch auf die **Richtlinienauswahl** Seite. Ein Warnsymbol neben einer Richtlinie weist darauf hin, dass die Richtlinie Skripts enthält.  
  
5.  Klicken Sie auf **auswerten** Auswertung die Richtlinien.  
  
     In der **Ergebnisse** Tabelle, die Ergebnisse für jede Richtlinie aufgeführt. Ein rotes "x"-Symbol gibt an, dass die Richtlinie nicht eingehalten wurde.  
  
6.  Bei einigen Richtlinienfehlern ermöglicht die richtlinienbasierte Verwaltung Ihnen, sofortige Richtlinieneinhaltung auf dem Ziel zu erzwingen. Im Fall eines solchen Fehlers wird ein Kontrollkästchen neben der fehlerhaften Richtlinie angezeigt. Wenn Sie die Kontrollkästchen der **übernehmen** Schaltfläche ist verfügbar. Beim Klicken auf **übernehmen**, die nicht kompatible Einstellung automatisch auf der Zielinstanz aktualisiert.  
  
    > [!CAUTION]  
    >  Bevor Sie eine Zielinstanz automatisch aktualisieren, sollten Sie die Richtlinieneinstellung vollständig verstanden haben. Es wird empfohlen, nachdem Sie eine oder mehrere Kontrollkästchen ausgewählt haben, Sie klicken **Skript**, und wählen Sie einen Ausgabespeicherort damit können Sie die zugrunde liegende überprüfen [!INCLUDE[tsql](../includes/tsql-md.md)] code, bevor Sie die Änderungen zu übernehmen.  
  
7.  Um ausführliche Ergebnisse für eine Richtlinie anzuzeigen, klicken Sie auf die Richtlinie in der **Ergebnisse** Tabelle.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ausführen einer bedarfsgesteuerten Auswertung mithilfe von registrierten Servern](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  