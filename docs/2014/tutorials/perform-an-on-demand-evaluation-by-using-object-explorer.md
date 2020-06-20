---
title: Ausführen einer bedarfsgesteuerten Auswertung mithilfe Objekt-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: da56673e05c092c965554b76572ac3b0486d2110
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044157"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Ausführen einer bedarfsgesteuerten Auswertung mit dem Objekt-Explorer
  In dieser Aufgabe verwenden Sie den Objekt-Explorer, um eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien für [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] auf einer einzelnen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz auszuführen.  
  
> [!NOTE]  
>  Sie können Richtlinien auch mithilfe der registrierten Server auf einer einzelnen Instanz auswerten. Weitere Informationen finden Sie unter [Ausführen einer bedarfsgesteuerten Auswertung mithilfe registrierter Server](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Diese Lektion basiert auf der von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ausgeführten Version von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Wenn Sie eine Bedarfs gesteuerte Auswertung von Best Practices-Richtlinien für Instanzen mit ausführen möchten [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] , müssen Sie das Verfahren im Thema [Ausführen einer bedarfsgesteuerten Auswertung mithilfe von registrierten Servern](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)verwenden.  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>So führen Sie eine bedarfsgesteuerte Auswertung mit dem Objekt-Explorer aus  
  
1.  Starten Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], und stellen Sie dann eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Erweitern Sie in Objekt-Explorer den Knoten **Verwaltung**, erweitern Sie **Richtlinien Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinien**, und klicken Sie auf **Auswerten**  
  
    > [!NOTE]  
    >  Standardmäßig wird die lokale Instanz als Quelle der Richtlinien verwendet. Wenn Sie zuvor Best Practices-Richtlinien importiert haben, werden diese zusammen mit anderen, von Ihnen erstellten Richtlinien aufgeführt. Sie können alle importierten Best Practices-Richtlinien auswählen und dann auf **Auswerten**klicken. Falls Sie keine Best Practices-Richtlinien importiert haben, fahren Sie mit dieser Prozedur fort.  
  
3.  Klicken Sie im Dialogfeld **Richtlinien auswerten** neben dem Feld **Quelle** auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
4.  Im Dialogfeld **Quelle auswählen** können Sie entweder **Dateien** oder **Server** als Quelle der auszuwertenden Richtlinien Dateien auswählen. Wenn Sie auf **Server**klicken, können Sie eine Bedarfs gesteuerte Auswertung aller Best Practices-Richtlinien durchführen, die zuvor in die Richtlinien basierte Verwaltung auf einem lokalen Server oder Remote Server importiert wurden. In diesem Tutorial klicken Sie auf **Dateien**und wählen dann die einzelnen Richtlinien Dateien aus, die Sie auswerten möchten. Gehen Sie dazu folgendermaßen vor:  
  
    1.  Klicken Sie auf **Dateien**.  
  
    2.  Klicken Sie neben **Dateien**auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
    3.  Navigieren Sie im Dialogfeld **Richtlinie auswählen** zum folgenden Ordner, in dem die Best Practices-Richtlinien enthalten sind:  
  
         **C:\Programme (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Abhängig davon, wo die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Programmdateien installiert sind, ob ein 32-Bit- oder 64-Bit-Betriebssystem ausgeführt bzw. ein Sprachbezeichner verwendet wird, kann sich der Dateipfad ändern.  
  
    4.  Wählen Sie eine oder mehrere XML-Richtlinien Dateien aus, die ausgewertet werden sollen, und klicken Sie dann auf **Öffnen**.  
  
         Die Liste der ausgewählten Dateien wird im Feld **Dateien** angezeigt.  
  
    5.  Klicken Sie im Dialogfeld **Quelle auswählen** auf **OK**.  
  
    6.  Wenn das Dialogfeld **Richtlinien laden** angezeigt wird, klicken Sie auf **Schließen**.  
  
     Die Richtlinien, die Sie ausgewählt haben, werden auf der Seite **Richtlinien Auswahl** aufgelistet. Ein Warnsymbol neben einer Richtlinie weist darauf hin, dass die Richtlinie Skripts enthält.  
  
5.  Klicken Sie auf **Auswerten** , um die Richtlinien auszuwerten.  
  
     In der **Ergebnis** Tabelle werden die Ergebnisse für jede Richtlinie aufgelistet. Ein rotes "x"-Symbol gibt an, dass die Richtlinie nicht eingehalten wurde.  
  
6.  Bei einigen Richtlinienfehlern ermöglicht die richtlinienbasierte Verwaltung Ihnen, sofortige Richtlinieneinhaltung auf dem Ziel zu erzwingen. Im Fall eines solchen Fehlers wird ein Kontrollkästchen neben der fehlerhaften Richtlinie angezeigt. Wenn Sie das Kontrollkästchen aktivieren, wird die Schaltfläche **anwenden** verfügbar. Wenn Sie auf **anwenden**klicken, wird die nicht kompatible Einstellung automatisch auf der Ziel Instanz aktualisiert.  
  
    > [!CAUTION]  
    >  Bevor Sie eine Zielinstanz automatisch aktualisieren, sollten Sie die Richtlinieneinstellung vollständig verstanden haben. Wir empfehlen, dass Sie nach dem Aktivieren eines oder mehrerer Kontrollkästchen auf **Skript**klicken und einen Ausgabe Speicherort auswählen, damit Sie den zugrunde liegenden Code überprüfen können, [!INCLUDE[tsql](../includes/tsql-md.md)] bevor Sie die Änderungen anwenden.  
  
7.  Um ausführliche Ergebnisse für eine Richtlinie anzuzeigen, klicken Sie auf die Richtlinie in der Tabelle **Ergebnisse** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ausführen einer bedarfsgesteuerten Auswertung mithilfe von registrierten Servern](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
