---
title: Reporting Services der Authentifizierung im SharePoint-Modus | Microsoft-Dokumentation
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
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ff0a4f38bf9ee7d9c27fbc07308084ed3272f95d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952102"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentifizierung im SharePoint-Modus von Reporting Services
  Verwenden Sie die Seite für die **** Authentifizierung im SharePoint-Modus von Reporting Services des Installations-Assistenten für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Anmeldeinformationen des in der aktuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendeten Dienstkontos anzugeben. Die Anmeldeinformationen werden zum Erstellen eines neuen SharePoint-Anwendungspools verwendet. Darüber hinaus wird eine neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -SharePoint-Dienstanwendung erstellt. Der Name der Dienstanwendung enthält den Namen der vorherigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz.  
  
## <a name="options"></a>Tastatur  
  
-   Die Option **Name des SSRS-Anwendungspoolkontos:** ist schreibgeschützt. Der Wert wird automatisch durch den aktuellen Wert aus der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation ersetzt, die Sie aktualisieren.  
  
-   Falls das Anwendungspoolkonto kein Kennwort erfordert, ist die Option **Kennwort des SSRS-Anwendungspoolkontos:** deaktiviert. Beispiel: "NT-Autorität \ NetworkService". Falls für das Anwendungspoolkonto ein Kennwort erforderlich ist, kann das Upgrade erst nach Eingabe des richtigen Kennworts fortgesetzt werden.  
  
 Weitere Informationen finden Sie unter [aktualisieren und Migrieren](https://go.microsoft.com/fwlink/?LinkID=245628) vonhttps://go.microsoft.com/fwlink/?LinkID=245628)Reporting Services ().  
  
## <a name="see-also"></a>Weitere Informationen  
 [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
