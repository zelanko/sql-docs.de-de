---
title: Verwenden von Microsoft Internetinformationsdienste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c71babf933c2615e6c2464696c1023ccaf53dd7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282465"
---
# <a name="using-microsoft-internet-information-services"></a>Verwenden der Microsoft-Internetinformationsdienste
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn Sie Probleme beim Herstellen einer Verbindung innerhalb eines IIS-Skripts haben (insbesondere wenn Sie einen Ora-12641-Fehler erhalten), fügen Sie die folgende Zeile in die Datei "SQLnet. Ora" ein:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Dadurch werden die sicheren Network Services deaktiviert, sodass Sie eine Verbindung mithilfe der anonymen Authentifizierung herstellen können.
