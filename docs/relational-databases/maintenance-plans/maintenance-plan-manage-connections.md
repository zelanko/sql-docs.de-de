---
title: Wartungsplan (Verbindungen verwalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ca8eeb29be40b422669a90961a2241aacc7fa910
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784488"
---
# <a name="maintenance-plan-manage-connections"></a>Wartungsplan (Verbindungen verwalten)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Geben Sie mithilfe des Dialogfelds **Verbindungen verwalten** die Eigenschaften der von Wartungsplänen verwendeten Verbindungen an. Beim Erstellen eines Wartungsplans wird eine lokale Verbindung zu dem Server erstellt, auf dem Sie den Plan erstellt haben. Erstellen Sie mithilfe dieser Verbindung Tasks, von denen Vorgänge für diese lokale Verbindung ausgeführt werden. Gegebenenfalls können Sie mithilfe des Dialogfelds **Verbindungen verwalten** auch Verbindungen hinzufügen. Beim Konfigurieren werden zusätzlich hinzugefügte Verbindungen im Feld mit den Verbindungen für die jeweiligen Tasks angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Server**  
 Die Serverinstanz.  
  
 **Authentifizierung**  
 Gibt an, ob für die Verbindung die Windows-Authentifizierung oder die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wird.  

> [!IMPORTANT]  
> Das Paket befindet sich in der **msdb**-Datenbank mit **ProtectionLevel** auf **ServerStorage** festgelegt, sodass das Kennwort nicht in **msdb** verschlüsselt ist, wenn die *SQL Server-Authentifizierung* verwendet wird. Sie können die *SQL Server-Authentifizierung* verwenden, solange **msdb** geschützt ist, aber die Verwendung der *Windows-Authentifizierung* wird empfohlen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
