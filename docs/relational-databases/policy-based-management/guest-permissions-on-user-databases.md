---
title: Gastberechtigungen für Benutzerdatenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 366ee3f80bacbd1cf17bcec7ed0c4e04ce892277
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787978"
---
# <a name="guest-permissions-on-user-databases"></a>Gastberechtigungen für Benutzerdatenbanken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel bestimmt, ob der Gastbenutzer die Berechtigung besitzt, auf die Datenbank zuzugreifen. Diese Regel gilt nur für Benutzerdatenbanken.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Widerrufen Sie die Gastbenutzerberechtigung für den Datenbankzugriff, wenn sie nicht erforderlich ist.  
  
 Der Gastbenutzer kann nicht gelöscht, aber deaktiviert werden. Zu diesem Zweck heben Sie die CONNECT-Berechtigung auf, indem Sie REVOKE CONNECT FROM GUEST in einer beliebigen Datenbank außer master, tempdb oder msdb ausführen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
