---
title: Führen Sie eine bedarfsgesteuerte Auswertung mithilfe von registrierten Servern | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f7deecbab3fceb117bfb3d237cf5940fdc34f5bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047532"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>Ausführen einer bedarfsgesteuerten Auswertung mithilfe von registrierten Servern
  Sie können eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien gegen eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe registrierter Server ausführen. Dazu können Sie lokale Servergruppen oder einen zentralen Verwaltungsserver verwenden.  
  
> [!NOTE]  
>  Sie können eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien gegen Servergruppenmitglieder ausführen, auf denen [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] oder eine höhere Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird. Wenn jedoch einige Eigenschaften vorhanden sind, auf die von einer in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] oder [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] nicht unterstützten Richtlinie verwiesen wird, kann ein Ausnahmefehler ausgegeben werden.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese Aufgabe auszuführen, müssen Sie mindestens eine Serverregistrierung in den registrierten Servern konfiguriert haben. Weitere Informationen finden Sie in folgenden Themen:  
  
-   [Erstellen oder Bearbeiten einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Registrieren eines verbundenen Servers &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
-   [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>So werten Sie Best Practices-Richtlinien gegen eine Servergruppe aus  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Registrierte Server**.  
  
2.  Erweitern Sie **Datenbankmodul**, und klicken Sie dann entweder den Unterpunkt **lokale Servergruppen**, oder **zentrale Verwaltungsserver**, abhängig von Ihrer Konfiguration.  
  
3.  Führen Sie eine der folgenden Aktionen aus:  
  
    -   Um die Richtlinien für alle Server, die von der lokalen Servergruppe verwaltet werden oder den zentralen Verwaltungsserver auswerten, mit der rechten Maustaste den Namen des lokalen Servers-Gruppe oder der Name des zentralen Verwaltungsservers, und klicken Sie dann auf **Richtlinien auswerten** .  
  
        > [!NOTE]  
        >  Wenn Sie Richtlinien mit einem zentralen Verwaltungsserver auswerten, werden diese nicht gegen den zentralen Verwaltungsserver selbst ausgewertet.  
  
    -   Zur Auswertung der Richtlinien für einen bestimmten Server oder eine Servergruppe, erweitern Sie **lokale Servergruppen** oder den zentralen Verwaltungsserver Benennen der rechten Maustaste auf den Server oder eine Servergruppe, die Sie verwenden möchten, Auswertung Richtlinien für, und klicken Sie dann auf **Richtlinien auswerten**.  
  
4.  In der **Richtlinien auswerten** Dialogfeld neben der **Quelle** klicken Sie auf die Auslassungspunkte (**...** ) Schaltfläche.  
  
5.  In der **Quelle auswählen** (Dialogfeld), wählen Sie entweder **Dateien** oder **Server** als Quelle der auszuwertenden Richtliniendateien. Wenn Sie auf **Server**, führen Sie eine bedarfsgesteuerte Auswertung von besten Practices-Richtlinien, die zuvor in die Richtlinie der richtlinienbasierten Verwaltung auf einem lokalen oder remote-Server importiert wurden. In diesem Lernprogramm klicken Sie auf **Dateien**, und wählen Sie dann die einzelnen Richtliniendateien aus, die Sie auswerten möchten. Führen Sie hierzu folgende Schritte aus:  
  
    1.  Klicken Sie auf **Dateien**.  
  
    2.  Neben **Dateien**, klicken Sie auf die Auslassungspunkte (**...** ) Schaltfläche.  
  
    3.  Wählen Sie eine oder mehrere XML-Richtliniendateien ausgewertet, und klicken Sie auf **öffnen**.  
  
         Die Liste der ausgewählten Dateien wird angezeigt, der **Dateien** Feld.  
  
    4.  In der **Quelle auswählen** (Dialogfeld), klicken Sie auf **OK**.  
  
    5.  Wenn die **Richtlinien laden** Dialogfeld angezeigt wird, klicken Sie auf **schließen**.  
  
     Die Richtlinien, die Sie ausgewählt haben, werden auch auf die **Richtlinienauswahl** Seite. Ein Warnsymbol neben einer Richtlinie weist darauf hin, dass die Richtlinie Skripts enthält.  
  
6.  Klicken Sie auf **auswerten** Auswertung die Richtlinien.  
  
7.  Bei einigen Richtlinienfehlern ermöglicht die richtlinienbasierte Verwaltung Ihnen, sofortige Richtlinieneinhaltung auf dem Ziel zu erzwingen. Im Fall eines solchen Fehlers wird ein Kontrollkästchen neben der fehlerhaften Richtlinie angezeigt. Wenn Sie das Kontrollkästchen, oder klicken Sie auf die Zeile mit der fehlerhaften Richtlinie, Kontrollkästchen angezeigt werden, der **Zieldetails** Bereich neben den Zielinstanzen, die die Auswertung fehlschlug. Wenn keines der Kontrollkästchen ausgewählt sind, die **übernehmen** Schaltfläche ist verfügbar. Beim Klicken auf **übernehmen**, die nicht kompatible Einstellung wird automatisch aktualisiert werden, auf den Zielinstanzen, die Sie ausgewählt haben.  
  
    > [!CAUTION]  
    >  Bevor Sie eine Zielinstanz automatisch aktualisieren, sollten Sie die Richtlinieneinstellung vollständig verstanden haben. Es wird empfohlen, nachdem Sie eine oder mehrere Kontrollkästchen ausgewählt haben, Sie klicken **Skript**, und wählen Sie einen Ausgabespeicherort damit können Sie die zugrunde liegende überprüfen [!INCLUDE[tsql](../includes/tsql-md.md)] code, bevor Sie die Änderungen zu übernehmen.  
  
8.  Um ausführliche Ergebnisse für eine Richtlinie anzuzeigen, klicken Sie auf die Richtlinie in der **Ergebnisse** Tabelle. Die **Zieldetails** Tabelle zeigt die Details für jede Instanz.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Auswerten von Best Practices-Richtlinien auf der Basis eines Zeitplans](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  