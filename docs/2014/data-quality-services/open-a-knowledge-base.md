---
title: Öffnen einer Wissensdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0f55065d3c62d87b51af83a411e2ba302fcf0528
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481289"
---
# <a name="open-a-knowledge-base"></a>Öffnen einer Wissensdatenbank
  In diesem Thema wird beschrieben, wie eine vorhandene Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) geöffnet und auf die Domänenverwaltung, die Wissensermittlung und das Hinzufügen einer Abgleichsrichtlinie vorbereitet wird.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Um eine Wissensdatenbank zu öffnen, muss die Wissensdatenbank bereits erstellt und entweder veröffentlicht (wenn sie eine andere Person erstellt hat) oder geschlossen (wenn Sie sie erstellt haben) worden sein.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle "dqs_kb_editor" oder "dqs_administrator" in der DQS_MAIN-Datenbank verfügen, um eine Wissensdatenbank zu öffnen.  
  
##  <a name="Open"></a> Open a knowledge base  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Klicken Sie auf dem [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Wissensdatenbank öffnen**.  
  
3.  Wählen Sie eine Wissensdatenbank in der Tabelle aus. Die Domänen und die Abgleichsregeln in der Wissensdatenbank werden im rechten Bereich der Seite angezeigt.  
  
    > [!NOTE]  
    >  Sie können Vorgänge in einer Wissensdatenbank ausführen, indem Sie mit der rechten Maustaste auf die Wissensdatenbank in der Tabelle klicken. Sie können die Wissensdatenbank öffnen, unter einem anderen Namen speichern, entsperren, umbenennen, die Arbeit verwerfen oder die Eigenschaften der Wissensdatenbank anzeigen.  
  
4.  Wählen Sie unter **Aktivität auswählen**die Aktivität aus, die Sie für die Wissensdatenbank ausführen möchten:  
  
    -   Wählen Sie **Domänenverwaltung** aus, um die Bildschirme zu öffnen, die Sie verwenden können, um die Domänen in der Wissensdatenbank zu ändern.  
  
    -   Wählen Sie **Wissensermittlung** aus, um den Assistenten zum Analysieren eines Datenbeispiels und Auffüllen der Domänen in der Wissensdatenbank mit den Ergebnissen zu öffnen.  
  
    -   Wählen Sie **Abgleichsrichtlinie** aus, um eine Abgleichsrichtlinie zu erstellen und sie der Wissensdatenbank hinzuzufügen.  
  
5.  Klicken Sie auf **Öffnen**.  
  
    > [!NOTE]  
    >  Sie können die Wissensdatenbank auch öffnen, indem Sie mit der rechten Maustaste auf die Datenbank klicken und dann auf „Öffnen“ klicken. Durch andere Befehle im Kontextmenü können Sie die Wissensdatenbank unter einem anderen Namen speichern, entsperren, umbenennen, die Arbeit daran verwerfen oder die Eigenschaften der Wissensdatenbank anzeigen.  
  
    > [!NOTE]  
    >  Wenn Sie die Wissensdatenbank nicht öffnen können, da sie gesperrt wird, finden Sie weitere Informationen im Abschnitt unten.  
  
## <a name="open-a-recent-knowledge-base"></a>Öffnen einer zuletzt geöffneten Wissensdatenbank  
 Die fünf zuletzt geöffneten Wissensdatenbanken werden in der Liste **Zuletzt verwendete Wissensdatenbank** auf der DQS-Startseite angezeigt. So erhalten Sie die Möglichkeit, eine Wissensdatenbank zu öffnen, an der Sie vor kurzem gearbeitet haben, ohne die Seite **Wissensdatenbank öffnen** aufrufen zu müssen.  
  
-   Um eine nicht gesperrte Wissensdatenbank in der Liste zuletzt geöffneter Wissensdatenbanken zu öffnen, klicken Sie auf den Pfeil nach rechts für die Wissensdatenbank, und wählen Sie dann die Aktivität aus, in der Sie die Wissensdatenbank öffnen möchten.  
  
-   Um eine von Ihnen gesperrte Wissensdatenbank in der Liste zuletzt geöffneter Wissensdatenbanken zu öffnen, klicken Sie auf die Wissensdatenbank, um sie mit der Aktivität und der Seite zu öffnen, die in Klammern angegeben sind.  
  
-   Um eine von einer anderen Person gesperrte Wissensdatenbank in der Liste zuletzt geöffneter Wissensdatenbanken zu öffnen, kontaktieren Sie diese Person, und lassen Sie sie die Wissensdatenbank entsperren.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Öffnen einer Wissensdatenbank  
 Nachdem Sie eine Wissensdatenbank geöffnet haben, wird die Wissensdatenbank in den Status versetzt, der in der Statusspalte der Wissensdatenbanktabelle angezeigt wird. Für die Wissensermittlung und die Abgleichsrichtlinienaktivitäten wird die Wissensdatenbank auf einer bestimmten Assistentenseite geöffnet. Für die Domänenverwaltungsaktivität wird die Wissensdatenbank auf der Domänenverwaltungsseite geöffnet. Weitere Informationen zu den Statuswerten finden Sie unter [Durchführen der Wissensermittlung](../../2014/data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../../2014/data-quality-services/managing-a-domain.md) oder [Erstellen einer Abgleichsrichtlinie](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Locked"></a> Wenn die Wissensdatenbank gesperrt ist  
 Das Schlosssymbol in der ersten Spalte zeigt an, ob die Wissensdatenbank gesperrt ist. Der Name einer gesperrten Wissensdatenbank wird in roter Schrift dargestellt. Eine Wissensdatenbank, die von einem bestimmten Benutzer durch eine Wissensdatenbankaktivität geändert wird, wird als gesperrt markiert. Eine gesperrte Wissensdatenbank kann nicht von einem zweiten Benutzer bearbeitet werden. Der Benutzer, der an der Wissensdatenbank arbeitet, kann sie entsperren, indem er in der Tabelle auf der Seite „Wissensdatenbank öffnen“ mit der rechten Maustaste auf die Wissensdatenbank klickt und dann auf **Entsperren**klickt, oder indem er sie veröffentlicht. Wenn der Cursor auf einer gesperrten Wissensdatenbank positioniert wird, zeigt DQS einen Hinweis an, der anzeigt, wer die Wissensdatenbank wann gesperrt hat.  
  
##  <a name="State"></a> Status einer Wissensdatenbank  
 Das Statusfeld gibt an, in welcher Phase einer Aktivität sich die Wissensdatenbank befindet. Wenn Sie die Wissensdatenbank öffnen, wird sie in dieser Phase geöffnet.  
  
-   **\<Empty>**: Das Statusfeld einer Wissensdatenbank ist leer, wenn sie veröffentlicht wird, indem in der Domänenverwaltungsaktivität auf **Veröffentlichen** und **Yes – Publish the knowledge base and exit** (Ja – Wissensdatenbank veröffentlichen und beenden) geklickt wird.  
  
-   **In Arbeit:** Die Arbeit an der Wissensdatenbank wurde durch Klicken auf **Veröffentlichen** in der Domänenverwaltungsaktivität und auf **No – Save the work on the knowledge base and exit** (Nein – Wissensdatenbank speichern und beenden) gespeichert.  
  
-   **Domänenverwaltung:** Es wurden Daten für eine Domäne in die Wissensdatenbank eingegeben, die Wissensdatenbank wurde jedoch nicht veröffentlicht, und die Arbeit bleibt in der Domänenverwaltungsaktivität erhalten. Die Wissensermittlungsaktivität ist nicht verfügbar. Dieser Fall tritt auf, wenn Sie im Bildschirm **Domänenverwaltung** auf **Schließen** klicken.  
  
-   **Discovery – Mapping** (Ermittlung – Zuordnung): Die Wissensdatenbank wurde auf der Seite **Knowledge Base Management: Mapping** (Wissensdatenbankverwaltung: Zuordnung) geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungs- und die Abgleichsaktivitäten sind nicht verfügbar.  
  
-   **Discovery – Discover** (Ermittlung – Ermitteln): Die Wissensdatenbank wurde auf der Seite **Knowledge Base Management: Analyze** (Wissensdatenbankverwaltung: Analysieren) geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungsaktivität ist nicht verfügbar.  
  
-   **Discovery – Value Management** (Ermittlung – Werteverwaltung): Die Wissensdatenbank wurde auf der Seite **Knowledge Base Management: Manage Domain Terms** (Wissensdatenbankverwaltung: Domänenbegriffe verwalten) geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungsaktivität ist nicht verfügbar.  
  
-   **Abgleichsrichtlinie – Abgleichen:** Die Wissensdatenbank wurde auf der Seite **Abgleichsrichtlinie – Abgleichen** geschlossen. Die Wissensdatenbank ist gesperrt, und die Wissensermittlungs- und die Domänenverwaltungsaktivitäten sind nicht verfügbar.  
  
-   **Abgleichsrichtlinie – Abgleichsergebnisse:** Die Wissensdatenbank wurde auf der Seite **Abgleichsrichtlinie – Abgleichsergebnisse** geschlossen. Die Wissensdatenbank ist gesperrt, und die Wissensermittlungs- und die Domänenverwaltungsaktivitäten sind nicht verfügbar.  
  
  
