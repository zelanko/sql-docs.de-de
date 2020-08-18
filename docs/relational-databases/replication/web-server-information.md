---
description: Webserverinformationen
title: Webserverinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ba110489a2ec2623018563257953d764ef371c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88325955"
---
# <a name="web-server-information"></a>Webserverinformationen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Webserverinformationen sind erforderlich, um die Websynchronisierungsoption für die Mergereplikation zu verwenden. Informationen zur Konfiguration der Websynchronisierung finden Sie unter [Konfigurieren der Websynchronisierung](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="options"></a>Tastatur  
 **Webserveradresse**  
 Wenn Sie auf der Seite **FTP-Momentaufnahme und Internet** des Dialogfelds **Veröffentlichungseigenschaften** eine Webserveradresse angegeben haben, wird diese in diesem Feld als Standardwert angezeigt. Übernehmen Sie entweder den Standardwert, oder geben Sie eine vollqualifizierte Webserveradresse für den Server für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internetinformationsdienste (IIS, Internet Information Services) an, der diese Abonnements synchronisiert.  
  
 **Wie stellt der Abonnent eine Verbindung mit dem Webserver her?**  
 Geben Sie den für das Herstellen einer Verbindung mit dem Webserver verwendeten Authentifizierungstyp an. Sie sollten für Verbindungen mit dem IIS-Server in Zusammenhang mit Transport Layer Security (TLS), früher als Secure Sockets Layer (SSL) bezeichnet, die Standardauthentifizierung verwenden. Geben Sie bei Auswahl der Standardauthentifizierung den Anmeldenamen und das Kennwort ein, die beim Herstellen der Verbindung vom Abonnenten zum IIS-Server verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [Websynchronisierung für die Mergereplikation](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
