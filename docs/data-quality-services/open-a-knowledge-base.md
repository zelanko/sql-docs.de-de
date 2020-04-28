---
title: Öffnen einer Wissensdatenbank
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 91f5e7effe54b9955537d90d639a820b5428a5c3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75246009"
---
# <a name="open-a-knowledge-base"></a>Öffnen einer Wissensdatenbank

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird beschrieben, wie eine vorhandene Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) geöffnet und auf die Domänenverwaltung, die Wissensermittlung und das Hinzufügen einer Abgleichsrichtlinie vorbereitet wird.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Um eine Wissensdatenbank zu öffnen, muss die Wissensdatenbank bereits erstellt und entweder veröffentlicht (wenn sie eine andere Person erstellt hat) oder geschlossen (wenn Sie sie erstellt haben) worden sein.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle "dqs_kb_editor" oder "dqs_administrator" in der DQS_MAIN-Datenbank verfügen, um eine Wissensdatenbank zu öffnen.  
  
##  <a name="open-a-knowledge-base"></a><a name="Open"></a>Öffnen einer Wissensdatenbank  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../data-quality-services/run-the-data-quality-client-application.md)aus.  
  
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
  
##  <a name="follow-up-after-opening-a-knowledge-base"></a><a name="FollowUp"></a>Nachverfolgung: nach dem Öffnen einer Wissensdatenbank  
 Nachdem Sie eine Wissensdatenbank geöffnet haben, wird die Wissensdatenbank in den Status versetzt, der in der Statusspalte der Wissensdatenbanktabelle angezeigt wird. Für die Wissensermittlung und die Abgleichsrichtlinienaktivitäten wird die Wissensdatenbank auf einer bestimmten Assistentenseite geöffnet. Für die Domänenverwaltungsaktivität wird die Wissensdatenbank auf der Domänenverwaltungsseite geöffnet. Weitere Informationen zu den Statuswerten finden Sie unter [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../data-quality-services/managing-a-domain.md) oder [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="if-the-knowledge-base-is-locked"></a><a name="Locked"></a>Wenn die Wissensdatenbank gesperrt ist  
 Das Schlosssymbol in der ersten Spalte zeigt an, ob die Wissensdatenbank gesperrt ist. Der Name einer gesperrten Wissensdatenbank wird in roter Schrift dargestellt. Eine Wissensdatenbank, die von einem bestimmten Benutzer durch eine Wissensdatenbankaktivität geändert wird, wird als gesperrt markiert. Eine gesperrte Wissensdatenbank kann nicht von einem zweiten Benutzer bearbeitet werden. Der Benutzer, der an der Wissensdatenbank arbeitet, kann sie entsperren, indem er in der Tabelle auf der Seite „Wissensdatenbank öffnen“ mit der rechten Maustaste auf die Wissensdatenbank klickt und dann auf **Entsperren**klickt, oder indem er sie veröffentlicht. Wenn der Cursor auf einer gesperrten Wissensdatenbank positioniert wird, zeigt DQS einen Hinweis an, der anzeigt, wer die Wissensdatenbank wann gesperrt hat.  
  
##  <a name="state-of-a-knowledge-base"></a><a name="State"></a>Status einer Wissensdatenbank  
 Das Statusfeld gibt an, in welcher Phase einer Aktivität sich die Wissensdatenbank befindet. Wenn Sie die Wissensdatenbank öffnen, wird sie in dieser Phase geöffnet.  
  
-   Leeres>: das Status Feld für eine Wissensdatenbank ist leer, wenn die Wissensdatenbank veröffentlicht wurde, indem Sie in der Domänen Verwaltungs Aktivität auf **veröffentlichen** geklickt und auf Ja klicken, um **die Wissensdatenbank zu veröffentlichen und zu beenden**. ** \< **  
  
-   **In Arbeit**: die Arbeit an der Wissensdatenbank wurde gespeichert, indem Sie in der Domänen Verwaltungs Aktivität auf **veröffentlichen** geklickt haben, und klicken Sie **auf Nein-die Arbeit in der Wissensdatenbank speichern und beenden**.  
  
-   **Domänenverwaltung**: Daten wurden für eine Domäne in der Wissensdatenbank eingegeben, aber die Wissensdatenbank wurde nicht veröffentlicht, und die Arbeit bleibt in der Domänenverwaltungsaktivität erhalten. Die Wissensermittlungsaktivität ist nicht verfügbar. Dieser Fall tritt auf, wenn Sie im Bildschirm **Domänenverwaltung** auf **Schließen** klicken.  
  
-   **Ermittlung – Zuordnung**: Die Wissensdatenbank wurde auf der Seite **Wissensdatenbank-Verwaltung: Zuordnung** geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungs- und die Abgleichsaktivitäten sind nicht verfügbar.  
  
-   **Ermittlung – Ermitteln**: Die Wissensdatenbank wurde auf der Seite **Wissensdatenbank-Verwaltung: Analysieren** geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungsaktivität ist nicht verfügbar.  
  
-   Ermittlung/ **Wert-Verwaltung**: die Wissensdatenbank wurde auf der Seite **Wissensdatenbank-Verwaltung: Domänen Begriffe verwalten** geschlossen. Die Wissensdatenbank ist gesperrt, und die Domänenverwaltungsaktivität ist nicht verfügbar.  
  
-   **Abgleichsrichtlinie für Richtlinie**: die Wissensdatenbank wurde auf der Seite abgleichsrichtlinienabgleichsrichtlinie geschlossen. **Matching Policy - Matching Policy** Die Wissensdatenbank ist gesperrt, und die Wissensermittlungs- und die Domänenverwaltungsaktivitäten sind nicht verfügbar.  
  
-   **Übereinstimmende Ergebnisse der Richtlinien Übereinstimmung**: die Wissensdatenbank wurde auf der Seite **abgleichsergebnisergebnisse** geschlossen. Die Wissensdatenbank ist gesperrt, und die Wissensermittlungs- und die Domänenverwaltungsaktivitäten sind nicht verfügbar.  
  
  
