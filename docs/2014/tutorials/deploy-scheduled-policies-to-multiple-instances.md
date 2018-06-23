---
title: Bereitstellen geplanter Richtlinien auf mehreren Instanzen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8331f0f33874c5bfbd0811231dc2cacf494b1d89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150241"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>Bereitstellen geplanter Richtlinien auf mehreren Instanzen
  Mithilfe von registrierten Servern können Sie geplante Richtlinien von einem zentralen Ort aus auf verwalteten Servern bereitstellen. Sie können geplante Richtlinien entweder über eine lokale Servergruppe oder über einen zentralen Verwaltungsserver bereitstellen.  
  
 Dabei führen Sie die folgenden Schritte aus:  
  
1.  Exportieren Sie die Richtlinien, die Sie in der vorherigen Aufgabe geplant haben, in einen Ordner.  
  
2.  Stellen Sie die geplanten Richtlinien auf Zielinstanzen bereit, die über registrierte Server verwaltet werden.  
  
 Sie führen diese Aufgaben auf dem Computer durch, auf dem Sie auch die vorherigen Aufgaben dieser Lektion durchgeführt haben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für diese Aufgabe gelten die folgenden Voraussetzungen:  
  
-   Sie müssen die vorherigen Aufgaben dieser Lektion abgeschlossen haben.  
  
-   Auf den Instanzen, auf denen Sie die geplanten Richtlinien bereitstellen möchten, muss [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ausgeführt werden. Die Automatisierung erfordert, dass die Richtlinien lokal gespeichert werden. Dies wird für ältere [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Versionen als [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] nicht unterstützt.  
  
-   Die Server, auf dem Sie die geplanten Richtlinien bereitstellen möchten, müssen in registrierte Server registriert werden, entweder in der **lokale Servergruppen** oder **zentrale Verwaltungsserver** Knoten. Weitere Informationen finden Sie in folgenden Themen:  
  
    -   [Erstellen oder Bearbeiten einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [Registrieren eines verbundenen Servers &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
    -   [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>So exportieren Sie die geplanten Richtlinien als XML-Dateien  
  
1.  Erweitern Sie auf dem Server, auf dem Sie geplante Richtlinien, in der vorherigen Aufgabe konfiguriert **Management**, erweitern Sie **richtlinienverwaltung**, und klicken Sie dann auf **Richtlinien**.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Details zum Objekt-Explorer**.  
  
3.  In der **Details zum Objekt-Explorer** Bereich, wählen Sie alle geplanten Best practices-Richtlinien, die auf andere Server über registrierte Server bereitgestellt werden soll.  
  
    > [!NOTE]  
    >  Klicken Sie auf die **Kategorie** Spaltenüberschrift, um die Richtlinien nach Kategorie zu sortieren.  
  
4.  Mit der rechten Maustaste in der Auswahl, und klicken Sie dann auf **Richtlinie exportieren**.  
  
5.  Wenn Sie mehrere Richtlinien für den export ausgewählt haben die **Ordner** (Dialogfeld), wählen Sie einen Zielordner, oder erstellen Sie einen neuen Ordner. In dieser Lektion erstellen Sie einen neuen Ordner mit dem Pfad **C:\Scheduled_BP_Policies**, und klicken Sie dann auf **OK**.  
  
     Wenn Sie nur eine Richtlinie für den export ausgewählt. die **Richtlinie exportieren** Dialogfeld Feld, erstellen Sie einen neuen Ordner mit dem Pfad **C:\Scheduled_BP_Policies**, klicken Sie auf **öffnen**, und klicken Sie dann auf **Speichern**.  
  
     Die XML-Richtliniendateien werden am Speicherort des Ordners erstellt.  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>So stellen Sie die geplanten Richtlinien auf Servern bereit, die über registrierte Server verwaltet werden  
  
1.  Klicken Sie im Menü **Ansicht** auf **Registrierte Server**.  
  
2.  Erweitern Sie **Datenbankmodul**, erweitern Sie entweder **lokale Servergruppen** oder **zentrale Verwaltungsserver**, mit der rechten Maustaste des Knotens, der Sie die Richtlinien bereitstellen möchten und klicken Sie dann Klicken Sie auf **Richtlinien importieren**.  
  
    > [!NOTE]  
    >  Wenn Sie mit der rechten Maustaste **lokale Servergruppen** oder den zentralen Verwaltungsserver selbst, die Richtlinien werden auf allen verwalteten Servern bereitgestellt werden. Falls Sie mit der rechten Maustaste auf eine bestimmte Servergruppe klicken, werden die Richtlinien nur auf den Servern dieser Gruppe bereitgestellt. Falls Sie mit der rechten Maustaste auf einen bestimmten registrierten Server klicken, werden die Richtlinien nur auf diesem Server bereitgestellt.  
  
3.  Neben **zu importierende Dateien**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...** ).  
  
4.  In der **Richtlinie auswählen** (Dialogfeld), navigieren Sie zu dem Ordner, in dem Sie die geplanten Richtlinien gespeichert. Navigieren Sie zum Speicherort, in diesem Beispiel **C:\Scheduled_BP_Policies**.  
  
5.  Wählen Sie die Richtlinien, die Sie verwenden möchten, auf die Zielinstanzen importieren, und klicken Sie dann auf **öffnen**.  
  
6.  In der **Import** Dialogfeld die **Richtlinienstatus** wählen den gewünschten Richtlinienstatus. Sie können wählen, ob Sie den Richtlinienstatus beim Importieren beibehalten oder die Richtlinien aktivieren bzw. deaktivieren möchten. Denken Sie daran, dass die Richtlinien aktiviert sein müssen, wenn sie nach einem Zeitplan ausgeführt werden sollen.  
  
7.  Klicken Sie auf **OK** auf die Richtlinien auf alle Zielinstanzen zu importieren.  
  
    > [!NOTE]  
    >  Wenn Fehler vorliegen, die **Import** Dialogfeld nicht ausgeblendet. Klicken Sie auf die **Protokoll** Seite, um die Meldungen zu prüfen. Klicken Sie auf **"Abbrechen"** um das Dialogfeld zu schließen.  
  
8.  Um die Richtlinien von einer Zielinstanz anzuzeigen, eine Verbindung mit der Instanz, Objekt-Explorer öffnen, erweitern Sie **Management**, und erweitern Sie dann **Richtlinien**. Daraufhin sollte die importierten Richtlinien der **Richtlinien** Knoten. Sie können jeweils den Zeitplan anzeigen, indem Sie auf die einzelnen Richtlinien doppelklicken, oder Sie können die Einstellungen ändern.  
  
    > [!NOTE]  
    >  Um nach der Ausführung einer geplanten Richtlinie die Auswertungsergebnisse anzuzeigen, öffnen Sie auf der Zielinstanz das Protokoll zum Richtlinienverlauf. Öffnen das Protokoll, mit der Maustaste **richtlinienverwaltung**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
## <a name="summary"></a>Zusammenfassung  
 In diesem Lernprogramm wurde gezeigt, wie Sie für eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bedarfsgesteuerte und geplante Auswertungen der Best Practices-Richtlinien durchführen.  
  
## <a name="next"></a>Weiter  
 Dieses Lernprogramm ist beendet. Um zum Start zurückzukehren, finden Sie unter [Lernprogramm: Auswerten von Best Practices mit der richtlinienbasierten Verwaltung](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).  
  
 Um eine Liste der finden Sie unter [!INCLUDE[ssDE](../includes/ssde-md.md)] Lernprogramme, klicken Sie auf [Lernprogramme zum Datenbankmodul](../relational-databases/database-engine-tutorials.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  