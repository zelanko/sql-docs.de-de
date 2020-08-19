---
description: 'Internetserverfehler: Zugriff verweigert'
title: 'Internet Server Fehler: Zugriff verweigert | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
author: rothja
ms.author: jroth
ms.openlocfilehash: 970c9c09946cebe74684e6aecc997e56213b1a97
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452172"
---
# <a name="internet-server-error-access-denied"></a>Internetserverfehler: Zugriff verweigert
Wenn Sie diesen Fehler erhalten, bedeutet dies in der Regel, dass Microsoft Internetinformationsdienste (IIS) den folgenden Status zurückgegeben hat:  
  
 HTTP_STATUS_DENIED 401  
  
 Stellen Sie sicher, dass die Verzeichnisse, auf die IIS zugreifen, über die entsprechenden RDS kann mit einem IIS-Webserver kommunizieren, der in einem der drei Kenn Wort Authentifizierungs Modi ausgeführt wird: anonym, Standard oder NT Challenge/Response (in Windows 2000 als integrierte Windows-Authentifizierung bezeichnet). Außerdem muss der Webserver über Berechtigungen für den Datenquellen Computer verfügen, sofern es sich um einen Windows NT/Windows 2000-Computer handelt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




