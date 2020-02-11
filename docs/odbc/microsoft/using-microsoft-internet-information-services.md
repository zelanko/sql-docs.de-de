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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9e531149af21facd80e9e6ddab19a76c3bdc0fa6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088145"
---
# <a name="using-microsoft-internet-information-services"></a>Verwenden der Microsoft-Internetinformationsdienste
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn Sie Probleme beim Herstellen einer Verbindung innerhalb eines IIS-Skripts haben (insbesondere wenn Sie einen Ora-12641-Fehler erhalten), fügen Sie die folgende Zeile in die Datei "SQLnet. Ora" ein:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Dadurch werden die sicheren Network Services deaktiviert, sodass Sie eine Verbindung mithilfe der anonymen Authentifizierung herstellen können.
