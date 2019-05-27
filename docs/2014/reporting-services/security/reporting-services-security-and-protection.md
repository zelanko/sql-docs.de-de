---
title: Sicherheit und Schutz für Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f8c7a4186c5236260fb27d8de107ce8c97bd363
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66101973"
---
# <a name="reporting-services-security-and-protection"></a>Sicherheit und Schutz für Reporting Services
  In diesem Abschnitt wird beschrieben, welche Sicherheitsfunktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. In diesem Abschnitt werden auch die Autorisierungsmodelle und die Authentifizierungsanbieter erläutert, die in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützt werden.  
  
## <a name="extended-protection-for-authentication"></a>Erweiterter Schutz für die Authentifizierung  
 Der erweiterte Schutz für die Authentifizierung wird ab [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]unterstützt. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktion unterstützt die Verwendung der Kanalbindung und Dienstbindung, um den Authentifizierungsschutz zu verbessern. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen müssen mit einem Betriebssystem verwendet werden, das erweiterten Schutz unterstützt. Weitere Informationen finden Sie unter [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Authentifizierung und Autorisierung  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet unterschiedliche Authentifizierungstypen für Benutzer und Clientanwendungen zur Authentifizierung mit dem Berichtsserver. Mit dem richtigen Authentifizierungstyp für Ihren Berichtsserver kann Ihr Unternehmen die den Anforderungen entsprechende Sicherheitsstufe erzielen. Weitere Informationen finden Sie unter [Authentication with the Report Server](authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet auch Rollen und Berechtigungen, um den Benutzerzugriff auf Inhalte des Berichtsserverkatalogs (d.h. wer worauf und wie zugreifen kann) zu steuern. Weitere Informationen finden Sie unter [Rollen und Berechtigungen &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibungen|Links|  
|-----------------------|-----------|  
|Konfigurieren Sie das Secure Sockets Layer (SSL), um Clientverbindungen zum Berichtsserver zu sichern.|[Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
