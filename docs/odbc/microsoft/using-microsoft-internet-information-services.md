---
title: Mit Microsoft Internet Information Services | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088145"
---
# <a name="using-microsoft-internet-information-services"></a>Verwenden der Microsoft-Internetinformationsdienste
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Wenn Sie schwierigkeiten bei der Herstellen einer Verbindung von innerhalb eines IIS-Skripts (insbesondere, wenn Sie Fehler ORA-12641 erhalten), fügen Sie die folgende Zeile in die Datei Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Dadurch wird die sichere Netzwerkdienste deaktiviert, damit Sie mit dem Verwenden der anonymen Authentifizierung herstellen können.
