---
title: Authentifizierung im SharePoint-Modus von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c932d8d75ee33bc0a0970f858a0a04f9b522e4ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092595"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentifizierung im SharePoint-Modus von Reporting Services
  Verwenden Sie die Seite für die **Authentifizierung im SharePoint-Modus von Reporting Services** des Installations-Assistenten für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Anmeldeinformationen des in der aktuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendeten Dienstkontos anzugeben. Die Anmeldeinformationen werden zum Erstellen eines neuen SharePoint-Anwendungspools verwendet. Darüber hinaus wird eine neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -SharePoint-Dienstanwendung erstellt. Der Name der Dienstanwendung enthält den Namen der vorherigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz.  
  
## <a name="options"></a>Optionen  
  
-   Die Option **Name des SSRS-Anwendungspoolkontos:** ist schreibgeschützt. Der Wert wird automatisch durch den aktuellen Wert aus der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation ersetzt, die Sie aktualisieren.  
  
-   Falls das Anwendungspoolkonto kein Kennwort erfordert, ist die Option **Kennwort des SSRS-Anwendungspoolkontos:** deaktiviert. Zum Beispiel "NT Authority\NetworkService". Falls für das Anwendungspoolkonto ein Kennwort erforderlich ist, kann das Upgrade erst nach Eingabe des richtigen Kennworts fortgesetzt werden.  
  
 Weitere Informationen finden Sie unter [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
