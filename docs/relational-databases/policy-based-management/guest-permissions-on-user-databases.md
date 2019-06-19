---
title: Gastberechtigungen für Benutzerdatenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: ec5e38c55ae31bac1cee4489f9e92065a649a748
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63006100"
---
# <a name="guest-permissions-on-user-databases"></a>Gastberechtigungen für Benutzerdatenbanken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel bestimmt, ob der Gastbenutzer die Berechtigung besitzt, auf die Datenbank zuzugreifen. Diese Regel gilt nur für Benutzerdatenbanken.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Widerrufen Sie die Gastbenutzerberechtigung für den Datenbankzugriff, wenn sie nicht erforderlich ist.  
  
 Der Gastbenutzer kann nicht gelöscht, aber deaktiviert werden. Zu diesem Zweck heben Sie die CONNECT-Berechtigung auf, indem Sie REVOKE CONNECT FROM GUEST in einer beliebigen Datenbank außer master, tempdb oder msdb ausführen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
