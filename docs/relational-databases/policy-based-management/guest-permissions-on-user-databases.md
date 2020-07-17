---
title: Gastberechtigungen für Benutzerdatenbanken | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie bestimmen, ob ein Gastbenutzer über die Berechtigungen für den Zugriff auf Benutzerdatenbanken in SQL Server verfügt. Außerdem erfahren Sie, wie Sie die Gastbenutzerberechtigung widerrufen, wenn sie nicht erforderlich ist.
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
ms.openlocfilehash: b6a911c84574c0b064c1c71bf9ff68aa725fc9c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749376"
---
# <a name="guest-permissions-on-user-databases"></a>Gastberechtigungen für Benutzerdatenbanken
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel bestimmt, ob der Gastbenutzer die Berechtigung besitzt, auf die Datenbank zuzugreifen. Diese Regel gilt nur für Benutzerdatenbanken.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Widerrufen Sie die Gastbenutzerberechtigung für den Datenbankzugriff, wenn sie nicht erforderlich ist.  
  
 Der Gastbenutzer kann nicht gelöscht, aber deaktiviert werden. Zu diesem Zweck heben Sie die CONNECT-Berechtigung auf, indem Sie REVOKE CONNECT FROM GUEST in einer beliebigen Datenbank außer master, tempdb oder msdb ausführen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
