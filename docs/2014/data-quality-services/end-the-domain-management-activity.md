---
title: Beenden der Domänen Verwaltungs Aktivität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16e030b52e4c7f99368efd8054f87df495b67257
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937711"
---
# <a name="end-the-domain-management-activity"></a>Beenden der Domänenverwaltungsaktivität
  In diesem Thema wird beschrieben wie die Domänenverwaltungsaktivität in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) abgeschlossen, geschlossen oder abgebrochen wird. Die Domänenverwaltung wird nicht von einem Assistenten durchgeführt. Daher können die unten beschriebenen Steuerelemente auf allen Seiten der Domänenverwaltungsaktivität verwendet werden.  
  
## <a name="end-domain-management"></a>Beenden der Domänenverwaltung  
 **Fertig stellen**  
 Klicken Sie auf diese Schaltfläche, um die Domänenverwaltung abzuschließen. Ein Popupfenster mit den folgenden Optionen wird angezeigt:  
  
-   **Ja – Wissensdatenbank veröffentlichen und beenden**: Die Wissensdatenbank wird veröffentlicht und kann vom aktuellen Benutzer oder von anderen Benutzern verwendet werden. Die Wissensdatenbank wird nicht gesperrt, der Status der Wissensdatenbank (in der Wissensdatenbanktabelle) wird auf leer festgelegt, und die Aktivitäten für die Domänenverwaltung sowie die Wissensermittlung sind verfügbar. Sie kehren zur Seite „Wissensdatenbank öffnen“ zurück.  
  
-   **Nein, die Arbeit in der Wissensdatenbank speichern und beenden**: Ihre Arbeit wird gespeichert, die Wissensdatenbank bleibt gesperrt, und der Status der Wissensdatenbank wird auf in Arbeit festgelegt. Sowohl die Domänenverwaltungs- als auch die Wissensermittlungsaktivitäten sind verfügbar. Sie kehren zur Startseite zurück.  
  
-   **Abbrechen-auf dem aktuellen Bildschirm bleiben**: das Popup Fenster wird geschlossen, und Sie werden zum Bildschirm "Domänen Verwaltung" zurückgegeben.  
  
 **Kündigen**  
 Klicken Sie auf diese Schaltfläche, um die Domänenverwaltungsaktivität abzubrechen, ohne die Arbeit zu speichern, und zur DQS-Startseite zurückzukehren.  
  
 **Close**  
 Klicken Sie auf diese Schaltfläche, um die Arbeit zu speichern, und kehren Sie zur DQS-Startseite zurück. Die Wissensdatenbank wird gesperrt, und der Status der Wissensdatenbank wird in der Wissensdatenbanktabelle auf der Seite **Wissensdatenbank öffnen** als **Domänenverwaltung**angezeigt. Nachdem Sie auf **Schließen**geklickt haben, um die Wissensermittlung durchzuführen, müssen Sie auf **Domänenverwaltung** klicken, auf **Fertig stellen**klicken und anschließend **Ja** (um die Wissensdatenbank zu veröffentlichen) oder **Nein** (um die Arbeit in der Wissensdatenbank zu speichern und zu beenden) auswählen.  Weitere Informationen zum Öffnen einer gesperrter Wissensdatenbank finden Sie unter [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
  
