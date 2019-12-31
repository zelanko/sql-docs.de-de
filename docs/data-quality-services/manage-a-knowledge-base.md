---
title: Verwalten einer Wissensdatenbank
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 1fda81ac39233435dbcd0546e452878cc6767b33
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247151"
---
# <a name="manage-a-knowledge-base"></a>Verwalten einer Wissensdatenbank

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird beschrieben, wie Verwaltungsfunktionen für eine Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ausgeführt werden. Sie können eine Wissensdatenbank löschen, entsperren, umbenennen, vorgenommene Anpassungen verwerfen und die Eigenschaften der Wissensdatenbank anzeigen.  
  
##  <a name="BeforeYouBegin"></a>Bevor Sie beginnen  
  
###  <a name="Prerequisites"></a>Voraussetzung  
 Um eine Wissensdatenbank zu verwalten, muss die Wissensdatenbank bereits erstellt und entweder veröffentlicht (wenn sie eine andere Person erstellt hat) oder geschlossen (wenn Sie sie erstellt haben) worden sein.  
  
###  <a name="Security"></a>Sicherung  
  
####  <a name="Permissions"></a>Griff  
 Sie müssen über die Rolle "dqs_kb_editor" oder "dqs_administrator" in der DQS_MAIN-Datenbank verfügen, um eine Wissensdatenbank zu öffnen.  
  
##  <a name="Manage"></a>Verwalten einer Wissensdatenbank  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie auf dem [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Wissensdatenbank öffnen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Wissensdatenbank in der Wissensdatenbanktabelle.  
  
4.  Im Kontextmenü können Sie folgende Schritte ausführen:  
  
    1.  **Öffnen**: Klicken Sie hier, um die Wissensdatenbank in der Aktivität zu öffnen, die im Bereich **Aktivität auswählen** ausgewählt ist.  
  
    2.  **Entsperren**: Sie können die Wissensdatenbank entsperren, wenn Sie der Benutzer sind, der in einem der Schritte der Domänen Verwaltung, der Wissens Ermittlung und der abgleichsrichtlinienaktivität an der Wissensdatenbank gearbeitet hat. Wenn Sie die Wissensdatenbank entsperren, kann sie von einer anderen Person geöffnet und bearbeitet werden. Dieser Befehl ist nicht verfügbar, wenn sich die Wissensdatenbank nicht in einem Aktivitätszustand befindet. Weitere Informationen finden Sie unter [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Arbeit verwerfen**: Klicken Sie auf, wenn sich die Wissensdatenbank in einem Zustand befindet, an dem die Wissensdatenbank bearbeitet wird, wie in einem Eintrag im Feld State in der Tabelle dargestellt. Dieser Befehl ist nicht verfügbar, wenn sich die Wissensdatenbank nicht in einem Aktivitätszustand befindet oder wenn die Wissensdatenbank gesperrt ist. Weitere Informationen finden Sie unter [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Umbenennen**: Klicken Sie hierauf, um das Feld Wissensdatenbank der Tabelle für die Wissensdatenbank, auf die Sie mit der rechten Maustaste geklickt haben, zu bearbeiten. Ändern Sie den Namen, und klicken Sie dann auf diese Wissensdatenbank und eine andere Wissensdatenbank in dem Feld, um die Namensänderung zu bestätigen.  
  
    5.  **Löschen**: Klicken Sie auf diese Option, um die Wissensdatenbank aus [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]der DQS_MAIN-Datenbank zu entfernen.  
  
    6.  **Eigenschaften**: Klicken Sie hierauf, um die Eigenschaften für die Datenbank in einer schreibgeschützten Anzeige anzuzeigen.  
  
        1.  **Quell-Wissensdatenbank**: die Wissensdatenbank, auf der diese Datenbank basiert. Dies ist optional.  
  
        2.  **State**: gibt an, ob die Wissensdatenbank **in Arbeit** ist und ob Sie sich in einer bestimmten Wissens Verwaltungs Aktivität befindet, die beim letzten schließen festgelegt wurde. Die Wissensdatenbank kann den Status **In Arbeit**haben – in dem Fall ist sie in einer Wissensverwaltungssitzung, jedoch nicht in einer bestimmten Aktivität geöffnet -, oder sie kann sich im Status **In Arbeit** sowie in einer Wissensverwaltungsaktivität befinden. In dem Fall ist die Wissensdatenbank in einer Wissensverwaltungssitzung und in einer bestimmten Aktivität geöffnet.  
  
        3.  **Ist gesperrt**: **true** , wenn die Wissensdatenbank gesperrt war, andernfalls **false** .  
  
        4.  **Enthält nicht veröffentlichten Inhalt**: true, wenn die Wissensdatenbank Inhalt enthält, der nicht durch Veröffentlichung gespeichert wurde, andernfalls false.  
  
        5.  **Gesperrt von**: der Name des Benutzers, der die Wissensdatenbank geschlossen hat, und sperrt ihn  
  
        6.  Sperr **Datum**: Datum der Sperrung  
  
        7.  **Erstellt von**: der Name des Benutzers, der die Wissensdatenbank erstellt hat, mit dem Netzwerk, zu dem er gehört.  
  
        8.  **Erstellungsdatum**: Datum der Erstellung  
  
##  <a name="FollowUp"></a>Nachverfolgung: nach dem Verwalten einer Wissensdatenbank  
 Der nächste Schritt nach dem Verwalten einer Wissensdatenbank hängt davon ab, welche Aktion Sie für die Wissensdatenbank durchgeführt haben:  
  
-   Wenn Sie die Wissensdatenbank geöffnet haben, fahren Sie mit der Aktivität fort, die Sie ausgewählt haben.  
  
-   Wenn Sie die Wissensdatenbank entsperrt haben, kann diese von einer anderen Person im angegebenen Status geöffnet und bearbeitet werden.  
  
-   Wenn Sie die Anpassungen der Wissensdatenbank verworfen haben, ist sie im zuletzt veröffentlichten Status verfügbar.  
  
-   Wenn Sie die Wissensdatenbank umbenannt haben, müssen Sie die Wissensdatenbank mit dem neuen Namen öffnen, um sie zu bearbeiten.  
  
-   Wenn Sie sie löschen, müssen Sie eine andere Wissensdatenbank für die Bearbeitung auswählen oder eine neue erstellen.  
  
  
