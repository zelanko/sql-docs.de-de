---
title: Bereitstellen geplanter Richtlinien auf mehreren Instanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8d37dafd5501a289e45a119323eed61242707184
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68185801"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>Bereitstellen geplanter Richtlinien auf mehreren Instanzen
  Mithilfe von registrierten Servern können Sie geplante Richtlinien von einem zentralen Ort aus auf verwalteten Servern bereitstellen. Sie können geplante Richtlinien entweder über eine lokale Servergruppe oder über einen zentralen Verwaltungsserver bereitstellen.  
  
 Dabei führen Sie die folgenden Schritte aus:  
  
1.  Exportieren Sie die Richtlinien, die Sie in der vorherigen Aufgabe geplant haben, in einen Ordner.  
  
2.  Stellen Sie die geplanten Richtlinien auf Zielinstanzen bereit, die über registrierte Server verwaltet werden.  
  
 Sie führen diese Aufgaben auf dem Computer durch, auf dem Sie auch die vorherigen Aufgaben dieser Lektion durchgeführt haben.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Für diese Aufgabe gelten die folgenden Voraussetzungen:  
  
-   Sie müssen die vorherigen Aufgaben dieser Lektion abgeschlossen haben.  
  
-   Auf den Instanzen, auf denen Sie die geplanten Richtlinien bereitstellen möchten, muss [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ausgeführt werden. Die Automatisierung erfordert, dass die Richtlinien lokal gespeichert werden. Dies wird für ältere [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Versionen als [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] nicht unterstützt.  
  
-   Die Server, auf denen Sie die geplanten Richtlinien bereitstellen möchten, müssen in den registrierten Servern entweder in den **lokalen Server Gruppen** oder im Knoten für **zentrale Verwaltungs Server** registriert sein. Weitere Informationen finden Sie in den folgenden Themen:  
  
    -   [Erstellen oder Bearbeiten einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [Registrieren Sie einen verbundenen Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
    -   [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>So exportieren Sie die geplanten Richtlinien als XML-Dateien  
  
1.  Erweitern Sie auf dem Server, auf dem Sie in der vorherigen Aufgabe geplante Richtlinien konfiguriert haben, **Verwaltung**, **Richtlinien Verwaltung**, und klicken Sie dann auf **Richtlinien**.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Details zum Objekt-Explorer**.  
  
3.  Wählen Sie im Bereich **Objekt-Explorer Details** alle geplanten Best Practices-Richtlinien aus, die Sie auf anderen Servern über registrierte Server bereitstellen möchten.  
  
    > [!NOTE]  
    >  Sie können auf die Überschrift der **Kategorie** klicken, um die Richtlinien nach Kategorie zu sortieren.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Auswahl, und klicken Sie auf **Richtlinie exportieren**.  
  
5.  Wenn Sie mehrere Richtlinien für den Export ausgewählt haben, wählen Sie im Dialogfeld **Ordner suchen** einen Zielordner aus, oder erstellen Sie einen neuen Ordner. Erstellen Sie für diese Lektion einen neuen Ordner mit dem Pfad **c:\ Scheduled_BP_Policies**, und klicken Sie dann auf **OK**.  
  
     Wenn Sie nur eine Richtlinie für den Export ausgewählt haben, erstellen Sie im Dialogfeld **Richtlinie exportieren** einen neuen Ordner mit dem Pfad **c:\ Scheduled_BP_Policies**, klicken Sie auf **Öffnen**, und klicken Sie dann auf **Speichern**.  
  
     Die XML-Richtliniendateien werden am Speicherort des Ordners erstellt.  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>So stellen Sie die geplanten Richtlinien auf Servern bereit, die über registrierte Server verwaltet werden  
  
1.  Klicken Sie im Menü **Ansicht** auf **Registrierte Server**.  
  
2.  Erweitern Sie **Datenbank-Engine**, erweitern Sie entweder **lokale Server Gruppen** oder **zentrale Verwaltungs Server**, klicken Sie mit der rechten Maustaste auf den Knoten, für den Sie die Richtlinien bereitstellen möchten, und klicken Sie dann auf **Richtlinien importieren**.  
  
    > [!NOTE]  
    >  Wenn Sie mit der rechten Maustaste auf **lokale Server Gruppen** oder den zentralen Verwaltungs Server selbst klicken, werden die Richtlinien auf allen verwalteten Servern bereitgestellt. Falls Sie mit der rechten Maustaste auf eine bestimmte Servergruppe klicken, werden die Richtlinien nur auf den Servern dieser Gruppe bereitgestellt. Falls Sie mit der rechten Maustaste auf einen bestimmten registrierten Server klicken, werden die Richtlinien nur auf diesem Server bereitgestellt.  
  
3.  Klicken Sie neben zu **importierende Dateien**auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
4.  Navigieren Sie im Dialogfeld **Richtlinie auswählen** zum Speicherort des Ordners, in dem Sie die geplanten Richtlinien gespeichert haben. Navigieren Sie in diesem Beispiel zum Speicherort **c:\ Scheduled_BP_Policies**.  
  
5.  Wählen Sie die Richtlinien aus, die Sie in die Ziel Instanzen importieren möchten, und klicken Sie dann auf **Öffnen**.  
  
6.  Wählen Sie im Dialogfeld **importieren** in der Liste **Richtlinien Status** den gewünschten Richtlinien Status aus. Sie können wählen, ob Sie den Richtlinienstatus beim Importieren beibehalten oder die Richtlinien aktivieren bzw. deaktivieren möchten. Denken Sie daran, dass die Richtlinien aktiviert sein müssen, wenn sie nach einem Zeitplan ausgeführt werden sollen.  
  
7.  Klicken Sie auf **OK** , um die Richtlinien in alle Ziel Instanzen zu importieren.  
  
    > [!NOTE]  
    >  Wenn Fehler auftreten, wird das Dialogfeld **importieren** nicht ausgeblendet. Klicken Sie auf die Seite **Protokoll** , um die Meldungen zu überprüfen. Klicken Sie auf **Abbrechen**, um das Dialogfeld zu schließen.  
  
8.  Um die Richtlinien von einer Ziel Instanz anzuzeigen, stellen Sie eine Verbindung mit der Instanz her, öffnen Sie Objekt-Explorer, erweitern Sie **Verwaltung**, und erweitern Sie dann **Richtlinien**. Die importierten Richtlinien sollten im Knoten **Richtlinien** angezeigt werden. Sie können jeweils den Zeitplan anzeigen, indem Sie auf die einzelnen Richtlinien doppelklicken, oder Sie können die Einstellungen ändern.  
  
    > [!NOTE]  
    >  Um nach der Ausführung einer geplanten Richtlinie die Auswertungsergebnisse anzuzeigen, öffnen Sie auf der Zielinstanz das Protokoll zum Richtlinienverlauf. Um das Protokoll zu öffnen, klicken Sie mit der rechten Maustaste auf **Richtlinien Verwaltung**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
## <a name="summary"></a>Zusammenfassung  
 In diesem Lernprogramm wurde gezeigt, wie Sie für eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bedarfsgesteuerte und geplante Auswertungen der Best Practices-Richtlinien durchführen.  
  
## <a name="next"></a>Next (Weiter)  
 Dieses Lernprogramm ist beendet. Um zum Anfang zurückzukehren, lesen Sie [Tutorial: auswerten bewährter Methoden mithilfe der Richtlinien basierten Verwaltung](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).  
  
 Um eine Liste der [!INCLUDE[ssDE](../includes/ssde-md.md)] Tutorials anzuzeigen, klicken Sie auf [Datenbank-Engine Tutorials](../relational-databases/database-engine-tutorials.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
