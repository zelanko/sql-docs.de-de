---
title: Beenden der Domänenverwaltungsaktivität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c0913ab07b006b845af081be0722da89f2ecd23
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515813"
---
# <a name="end-the-domain-management-activity"></a>Beenden der Domänenverwaltungsaktivität
  In diesem Thema wird beschrieben wie die Domänenverwaltungsaktivität in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) abgeschlossen, geschlossen oder abgebrochen wird. Die Domänenverwaltung wird nicht von einem Assistenten durchgeführt. Daher können die unten beschriebenen Steuerelemente auf allen Seiten der Domänenverwaltungsaktivität verwendet werden.  
  
## <a name="end-domain-management"></a>Beenden der Domänenverwaltung  
 **Fertig stellen**  
 Klicken Sie auf diese Schaltfläche, um die Domänenverwaltung abzuschließen. Ein Popupfenster mit den folgenden Optionen wird angezeigt:  
  
-   **Veröffentlichen Sie Ja – Wissensdatenbank und beenden**: Die Wissensdatenbank wird für den aktuellen Benutzer oder von anderen Benutzern verwenden veröffentlicht werden. Die Wissensdatenbank wird nicht gesperrt, der Status der Wissensdatenbank (in der Wissensdatenbanktabelle) wird auf leer festgelegt, und die Aktivitäten für die Domänenverwaltung sowie die Wissensermittlung sind verfügbar. Sie kehren zur Seite „Wissensdatenbank öffnen“ zurück.  
  
-   **Nein – Arbeit in die Wissensdatenbank, und Beenden speichern**: Ihre Arbeit wird gespeichert, die Wissensdatenbank bleibt gesperrt, und der Status der Wissensdatenbank wird auf Arbeit festgelegt werden. Sowohl die Domänenverwaltungs- als auch die Wissensermittlungsaktivitäten sind verfügbar. Sie kehren zur Startseite zurück.  
  
-   **Abbrechen – im aktuellen Fenster bleiben**: Das Popupfenster wird geschlossen, und Sie kehren zum Fenster "Domänenverwaltung".  
  
 **Abbrechen**  
 Klicken Sie auf diese Schaltfläche, um die Domänenverwaltungsaktivität abzubrechen, ohne die Arbeit zu speichern, und zur DQS-Startseite zurückzukehren.  
  
 **Schließen**  
 Klicken Sie auf diese Schaltfläche, um die Arbeit zu speichern, und kehren Sie zur DQS-Startseite zurück. Die Wissensdatenbank wird gesperrt, und der Status der Wissensdatenbank wird in der Wissensdatenbanktabelle auf der Seite **Wissensdatenbank öffnen** als **Domänenverwaltung**angezeigt. Nachdem Sie auf **Schließen**geklickt haben, um die Wissensermittlung durchzuführen, müssen Sie auf **Domänenverwaltung** klicken, auf **Fertig stellen**klicken und anschließend **Ja** (um die Wissensdatenbank zu veröffentlichen) oder **Nein** (um die Arbeit in der Wissensdatenbank zu speichern und zu beenden) auswählen.  Weitere Informationen zum Öffnen einer gesperrter Wissensdatenbank finden Sie unter [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
  
