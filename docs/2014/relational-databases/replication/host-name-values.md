---
title: HOST_NAME-Werte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f116033e54e33bc63893865bdc4339399dde4f4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100754"
---
# <a name="hostname-values"></a>HOST_NAME-Werte
  In Mergeveröffentlichungen mit parametrisierten Filtern werden zum Filtern der Daten die SUSER_SNAME()-Funktion und/oder die HOST_NAME()-Funktion verwendet. Die Funktion wird im Assistenten für neue Veröffentlichung oder im Dialogfeld **Veröffentlichungseigenschaften** angegeben.  
  
 Standardmäßig wird durch die HOST_NAME()-Funktion der Name des Computers zurückgegeben, der die Verbindung mit dem Verleger herstellt. Wenn Sie parametrisierte Filter verwenden, wird dieser Wert normalerweise überschrieben, indem Sie auf dieser Seite des Assistenten einen Wert bereitstellen. Daraufhin wird durch die HOST_NAME()-Funktion nicht der Name des Computers, sondern der von Ihnen angegebene Wert zurückgegeben. Weitere Informationen finden Sie im Abschnitt „Überschreiben des HOST_NAME()-Wertes“ in [Parametrisierte Zeilenfilter](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Wenn Sie HOST_NAME() überschreiben, wird für sämtliche Aufrufe der HOST_NAME()-Funktion der von Ihnen angegebene Wert zurückgegeben. Stellen Sie sicher, dass keine andere Anwendung darauf angewiesen ist, dass HOST_NAME() den Computernamen zurückgibt.  
  
## <a name="options"></a>Tastatur  
 **Abonnementeigenschaften**  
 Geben Sie in der **HOST_NAME Value** -Spalte für jeden Abonnenten einen Wert ein, oder übernehmen Sie den als Standardwert angegebenen Namen des Abonnentencomputers.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](view-and-modify-pull-subscription-properties.md)   
 [Anzeigen und Ändern der Eigenschaften von Pushabonnements](view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)   
 [Subscribe to Publications](subscribe-to-publications.md)  
  
  
