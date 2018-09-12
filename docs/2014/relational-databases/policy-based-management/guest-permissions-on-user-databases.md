---
title: Gastberechtigungen für Benutzerdatenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8416b7500ca68fe1a42ba2a8f2f3e57d81ec8ebc
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810016"
---
# <a name="guest-permissions-on-user-databases"></a>Gastberechtigungen für Benutzerdatenbanken
  Diese Regel bestimmt, ob der Gastbenutzer die Berechtigung besitzt, auf die Datenbank zuzugreifen. Diese Regel gilt nur für Benutzerdatenbanken.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Widerrufen Sie die Gastbenutzerberechtigung für den Datenbankzugriff, wenn sie nicht erforderlich ist.  
  
 Der Gastbenutzer kann nicht gelöscht, aber deaktiviert werden. Zu diesem Zweck heben Sie die CONNECT-Berechtigung auf, indem Sie REVOKE CONNECT FROM GUEST in einer beliebigen Datenbank außer master, tempdb oder msdb ausführen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sichern von SQL Server](../security/securing-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
