---
description: Wartungsplan (Server)
title: Wartungsplan (Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1a991404f0acaba448958773f54a4836032ecd07
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88420854"
---
# <a name="maintenance-plan-servers"></a>Wartungsplan (Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Mithilfe des Dialogfelds **Server** können Sie die Server auswählen, auf denen der Wartungsplan ausgeführt werden soll.  
  
 Es muss eine Multiserverumgebung mit einem Masterserver und mindestens einem Zielserver konfiguriert sein, um einen Multiserver-Wartungsplan erstellen zu können. Für Multiserver-Wartungspläne sollte der lokale Server als Masterserver konfiguriert werden. Bei Multiserverumgebungen werden in diesem Dialogfeld der **(lokale)** Masterserver und alle entsprechenden Zielserver angezeigt. Für den lokalen Server wird ein Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents erstellt. Er wird aktiviert oder deaktiviert, je nachdem, ob Sie den **(lokalen)** Server auswählen. Wenn Zielserver ausgewählt sind, wird für jeden ausgewählten Zielserver ein Multiserverauftrag erstellt und auf diesen heruntergeladen. Wenn keine Zielserver ausgewählt sind, wird der Multiserverauftrag gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Erstellen einer Multiserverumgebung](../../ssms/agent/create-a-multiserver-environment.md)   
 [Einrichten eines Masterservers](../../ssms/agent/make-a-master-server.md)   
 [Erstellen eines Zielservers](../../ssms/agent/make-a-target-server.md)  
  
  
