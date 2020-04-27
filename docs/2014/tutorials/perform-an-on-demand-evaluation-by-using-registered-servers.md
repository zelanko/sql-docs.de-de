---
title: Ausführen einer bedarfsgesteuerten Auswertung mithilfe registrierter Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a3a79a6ec655e91264d6fcc00db5a920ad82a21e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66822371"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>Ausführen einer bedarfsgesteuerten Auswertung mithilfe von registrierten Servern

  Sie können eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien gegen eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe registrierter Server ausführen. Dazu können Sie lokale Servergruppen oder einen zentralen Verwaltungsserver verwenden.  
  
> [!NOTE]  
>  Sie können eine bedarfsgesteuerte Auswertung von Best Practices-Richtlinien gegen Servergruppenmitglieder ausführen, auf denen [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] oder eine höhere Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird. Wenn jedoch einige Eigenschaften vorhanden sind, auf die von einer in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] oder [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] nicht unterstützten Richtlinie verwiesen wird, kann ein Ausnahmefehler ausgegeben werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um diese Aufgabe auszuführen, müssen Sie mindestens eine Serverregistrierung in den registrierten Servern konfiguriert haben. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Erstellen oder Bearbeiten einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Registrieren Sie einen verbundenen Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
-   [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>So werten Sie Best Practices-Richtlinien gegen eine Servergruppe aus  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Registrierte Server**.  
  
2.  Erweitern Sie **Datenbank-Engine**, und erweitern Sie dann abhängig von Ihrer Konfiguration entweder **lokale Server Gruppen**oder **zentrale Verwaltungs Server**.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie mit der rechten Maustaste auf den Namen der lokalen Server Gruppe oder den Namen der zentralen Management Server, und klicken Sie dann auf **Richtlinien auswerten**, um die Richtlinien für alle Server auszuwerten, die von der lokalen Server Gruppe oder der zentralen Management Server verwaltet werden.  
  
        > [!NOTE]  
        >  Wenn Sie Richtlinien mit einem zentralen Verwaltungsserver auswerten, werden diese nicht gegen den zentralen Verwaltungsserver selbst ausgewertet.  
  
    -   Wenn Sie die Richtlinien für einen bestimmten Server oder eine bestimmte Server Gruppe auswerten möchten, erweitern Sie **lokale Server Gruppen** oder den zentralen Management Server Namen, klicken Sie mit der rechten Maustaste auf den Server oder die Server Gruppe, für die Sie Richtlinien auswerten möchten, und klicken Sie dann auf **Richtlinien**  
  
4.  Klicken Sie im Dialogfeld **Richtlinien auswerten** neben dem Feld **Quelle** auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
5.  Im Dialogfeld **Quelle auswählen** können Sie entweder **Dateien** oder **Server** als Quelle der auszuwertenden Richtlinien Dateien auswählen. Wenn Sie auf **Server**klicken, können Sie eine Bedarfs gesteuerte Auswertung aller Best Practices-Richtlinien durchführen, die zuvor in die Richtlinien basierte Verwaltung auf einem lokalen Server oder Remote Server importiert wurden. In diesem Tutorial klicken Sie auf **Dateien**und wählen dann die einzelnen Richtlinien Dateien aus, die Sie auswerten möchten. Gehen Sie hierzu folgendermaßen vor:  
  
    1.  Klicken Sie auf **Dateien**.  
  
    2.  Klicken Sie neben **Dateien**auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
    3.  Wählen Sie eine oder mehrere XML-Richtlinien Dateien aus, die ausgewertet werden sollen, und klicken Sie dann auf **Öffnen**.  
  
         Die Liste der ausgewählten Dateien wird im Feld **Dateien** angezeigt.  
  
    4.  Klicken Sie im Dialogfeld **Quelle auswählen** auf **OK**.  
  
    5.  Wenn das Dialogfeld **Richtlinien laden** angezeigt wird, klicken Sie auf **Schließen**.  
  
     Die Richtlinien, die Sie ausgewählt haben, werden auf der Seite **Richtlinien Auswahl** aufgelistet. Ein Warnsymbol neben einer Richtlinie weist darauf hin, dass die Richtlinie Skripts enthält.  
  
6.  Klicken Sie auf **Auswerten** , um die Richtlinien auszuwerten.  
  
7.  Bei einigen Richtlinienfehlern ermöglicht die richtlinienbasierte Verwaltung Ihnen, sofortige Richtlinieneinhaltung auf dem Ziel zu erzwingen. Im Fall eines solchen Fehlers wird ein Kontrollkästchen neben der fehlerhaften Richtlinie angezeigt. Wenn Sie das Kontrollkästchen aktivieren oder auf die Zeile mit der fehlerhaften Richtlinie klicken, werden im Bereich **Ziel Details** neben den Ziel Instanzen, für die die Auswertung fehlgeschlagen ist, Kontrollkästchen angezeigt. Wenn eines der Kontrollkästchen aktiviert ist, wird die Schaltfläche **anwenden** verfügbar. Wenn Sie auf **anwenden**klicken, wird die nicht kompatible Einstellung automatisch auf den von Ihnen ausgewählten Ziel Instanzen aktualisiert.  
  
    > [!CAUTION]  
    >  Bevor Sie eine Zielinstanz automatisch aktualisieren, sollten Sie die Richtlinieneinstellung vollständig verstanden haben. Wir empfehlen, dass Sie nach dem Aktivieren eines oder mehrerer Kontrollkästchen auf **Skript**klicken und einen Ausgabe Speicherort auswählen, damit Sie den zugrunde liegenden [!INCLUDE[tsql](../includes/tsql-md.md)] Code überprüfen können, bevor Sie die Änderungen anwenden.  
  
8.  Um ausführliche Ergebnisse für eine Richtlinie anzuzeigen, klicken Sie auf die Richtlinie in der Tabelle **Ergebnisse** . In der Tabelle **Ziel Details** werden die Details für jede Instanz angezeigt.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Auswerten von Best Practices-Richtlinien auf Basis eines Zeitplans](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und erzwingen bewährter Methoden mithilfe der Richtlinien basierten Verwaltung](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
