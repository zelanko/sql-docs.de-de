---
title: 'Internetserverfehler: Zugriff verweigert. | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b7c562e57341dd027a4cd9bdc3a0fa4bbe51ae5
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558393"
---
# <a name="internet-server-error-access-denied"></a>Internetserverfehler: Zugriff verweigert
Wenn Sie diesen Fehler erhalten, bedeutet dies normalerweise, dass Microsoft Internet Information Services (IIS) die folgende Status zurückgegeben:  
  
 HTTP_STATUS_DENIED 401  
  
 Stellen Sie sicher, dass die Verzeichnisse, die von IIS Zugriff auf die entsprechenden Berechtigungen verfügen. RDS mit IIS-Webserver ausgeführt wird, in einem der drei Modi Kennwortauthentifizierung kommunizieren kann: Anonymous, Basic oder NT Challenge/Response (integrierte Windows-Authentifizierung in Windows 2000 genannt). Darüber hinaus muss der Web-Server Berechtigungen für den Quellcomputer Daten verfügen, wenn es sich um einen Windows NT/Windows 2000-Computer ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




