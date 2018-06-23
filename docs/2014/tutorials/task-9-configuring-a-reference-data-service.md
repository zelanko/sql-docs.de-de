---
title: 'Aufgabe 9: Konfigurieren ein Reference Data Service | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5a08d3848ddaf65b9e10b654f55e8a0a4d9be690
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163403"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Aufgabe 9: Konfigurieren eines Reference Data Service
  In dieser Aufgabe konfigurieren Sie DQS für die Verwendung eines Reference Data Service in Windows Azure Marketplace. In der nächsten Aufgabe Konfigurieren Sie die **Address Validation** Domäne, die diesen Dienst verwendet. Zur Laufzeit während der bereinigungsaktivität DQS übergibt die Werte der Domänen in der **Address Validation** Domäne zur Bereinigung an den Dienst. Finden Sie unter [Konfigurieren von DQS zum Verwenden von Verweisdaten](http://msdn.microsoft.com/library/hh213070.aspx) Weitere Details.  
  
1.  Auf der Hauptseite des **DQS-Client**in der **Verwaltung** Bereich, klicken Sie auf **Konfiguration**.  
  
2.  Sicherstellen, dass **Verweisdaten** Registerkarte aktiv ist.  
  
3.  In der **Netzwerkeinstellungen** Bereich, geben Sie entsprechende Werte in der **Proxyserver** und **Port** Felder, wenn Sie einen Proxyserver verwenden, um eine Verbindung zum Internet herstellen müssen.  
  
4.  Typ der **Windows Azure Marketplace-Kontoschlüssel** für die **DataMarket-Konto-ID** Feld.  
  
     ![Azure Data Markt-Verweisdatendienstkonto](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market Reference Data-Dienstkonto")  
  
5.  Klicken Sie auf **Validate** Schaltfläche neben dem Textfeld, um die Konto-ID zu überprüfen.  
  
6.  Klicken Sie auf **OK** im Meldungsfeld.  
  
7.  Klicken Sie auf **schließen** am unteren Rand der Seite, um zur Hauptseite des DQS-Client zu wechseln.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 [Aufgabe 10: Konfigurieren der Verbunddomäne, um Reference Data Service zu verwenden](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  