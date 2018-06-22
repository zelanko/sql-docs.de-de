---
title: Wartungsplan (Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 339282ab74dac6e77852fa6ecff21f5008e6842b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060493"
---
# <a name="maintenance-plan-servers"></a>Wartungsplan (Server)
  Mithilfe des Dialogfelds **Server** können Sie die Server auswählen, auf denen der Wartungsplan ausgeführt werden soll.  
  
 Es muss eine Multiserverumgebung mit einem Masterserver und mindestens einem Zielserver konfiguriert sein, um einen Multiserver-Wartungsplan erstellen zu können. Für Multiserver-Wartungspläne sollte der lokale Server als Masterserver konfiguriert werden. Bei Multiserverumgebungen werden in diesem Dialogfeld der **(lokale)** Masterserver und alle entsprechenden Zielserver angezeigt. Für den lokalen Server wird ein Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents erstellt. Er wird aktiviert oder deaktiviert, je nachdem, ob Sie den **(lokalen)** Server auswählen. Wenn Zielserver ausgewählt sind, wird für jeden ausgewählten Zielserver ein Multiserverauftrag erstellt und auf diesen heruntergeladen. Wenn keine Zielserver ausgewählt sind, wird der Multiserverauftrag gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [Wartungspläne](maintenance-plans.md)   
 [Erstellen einer Multiserverumgebung](../../ssms/agent/create-a-multiserver-environment.md)   
 [Einrichten eines Masterservers](../../ssms/agent/make-a-master-server.md)   
 [Erstellen eines Zielservers](../../ssms/agent/make-a-target-server.md)  
  
  