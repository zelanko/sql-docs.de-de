---
title: Verwenden von Datenbank-E-Mail anstelle von SQL Mail | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 091e8278e18cd5c4545bad31e0d5fec0a5c4c7fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32953725"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Verwenden von Datenbank-E-Mail anstelle von SQL Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft die sys.configurations-Katalogsicht, um zu bestimmen, ob die serverweite Konfigurationoption von SQL Mail XPs auf ON festgelegt ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 SQL Mail wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie zum Versenden von E-Mail-Nachrichten Datenbank-E-Mail.  
  
 SQL Mail wird prozessintern zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt. Wenn SQL Mail beendet wird, wird der Server ebenfalls beendet. Datenbank-E-Mail wird in einem separaten Prozess außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt. Sie ist skalierbar und benötigt keine Extended MAPI-Clientkomponenten auf dem Produktionsserver.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
