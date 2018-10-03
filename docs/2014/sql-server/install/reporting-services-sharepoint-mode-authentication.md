---
title: Authentifizierung im SharePoint-Modus von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5c4c0e1536a32fa5aca0bc63ec80e255ad755491
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185297"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentifizierung im SharePoint-Modus von Reporting Services
  Verwenden Sie die Seite für die **Authentifizierung im SharePoint-Modus von Reporting Services** des Installations-Assistenten für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Anmeldeinformationen des in der aktuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendeten Dienstkontos anzugeben. Die Anmeldeinformationen werden zum Erstellen eines neuen SharePoint-Anwendungspools verwendet. Darüber hinaus wird eine neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -SharePoint-Dienstanwendung erstellt. Der Name der Dienstanwendung enthält den Namen der vorherigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz.  
  
## <a name="options"></a>Tastatur  
  
-   Die Option **Name des SSRS-Anwendungspoolkontos:** ist schreibgeschützt. Der Wert wird automatisch durch den aktuellen Wert aus der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation ersetzt, die Sie aktualisieren.  
  
-   Falls das Anwendungspoolkonto kein Kennwort erfordert, ist die Option **Kennwort des SSRS-Anwendungspoolkontos:** deaktiviert. Beispiel: "NT Authority\NetworkService". Falls für das Anwendungspoolkonto ein Kennwort erforderlich ist, kann das Upgrade erst nach Eingabe des richtigen Kennworts fortgesetzt werden.  
  
 Weitere Informationen finden Sie unter [Upgrade and Migrate Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren und Migrieren von Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
