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
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059016"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentifizierung im SharePoint-Modus von Reporting Services
  Verwenden Sie die Seite für die **** Authentifizierung im SharePoint-Modus von Reporting Services des Installations-Assistenten für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Anmeldeinformationen des in der aktuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendeten Dienstkontos anzugeben. Die Anmeldeinformationen werden zum Erstellen eines neuen SharePoint-Anwendungspools verwendet. Darüber hinaus wird eine neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -SharePoint-Dienstanwendung erstellt. Der Name der Dienstanwendung enthält den Namen der vorherigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz.  
  
## <a name="options"></a>Optionen  
  
-   Die Option **Name des SSRS-Anwendungspoolkontos:** ist schreibgeschützt. Der Wert wird automatisch durch den aktuellen Wert aus der vorhandenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation ersetzt, die Sie aktualisieren.  
  
-   Falls das Anwendungspoolkonto kein Kennwort erfordert, ist die Option **Kennwort des SSRS-Anwendungspoolkontos:** deaktiviert. Beispiel: "NT-Autorität \ NetworkService". Falls für das Anwendungspoolkonto ein Kennwort erforderlich ist, kann das Upgrade erst nach Eingabe des richtigen Kennworts fortgesetzt werden.  
  
 Weitere Informationen finden Sie unter [aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) () https://go.microsoft.com/fwlink/?LinkID=245628) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren und Migrieren von Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
