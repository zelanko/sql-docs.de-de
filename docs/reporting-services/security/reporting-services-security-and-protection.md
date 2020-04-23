---
title: Sicherheit und Schutz für Reporting Services | Microsoft-Dokumentation
ms.date: 08/26/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 189c0d314ba3f16b00ad570b3e0f9fbce9fa2f7e
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632419"
---
# <a name="reporting-services-security-and-protection"></a>Sicherheit und Schutz für Reporting Services
  In diesem Abschnitt wird beschrieben, welche Sicherheitsfunktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. In diesem Abschnitt werden auch die Autorisierungsmodelle und die Authentifizierungsanbieter erläutert, die in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützt werden.  
  
## <a name="extended-protection-for-authentication"></a>Erweiterter Schutz für die Authentifizierung  
 Der erweiterte Schutz für die Authentifizierung wird ab [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]unterstützt. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktion unterstützt die Verwendung der Kanalbindung und Dienstbindung, um den Authentifizierungsschutz zu verbessern. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen müssen mit einem Betriebssystem verwendet werden, das erweiterten Schutz unterstützt. Weitere Informationen finden Sie unter [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Authentifizierung und Autorisierung  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet unterschiedliche Authentifizierungstypen für Benutzer und Clientanwendungen zur Authentifizierung mit dem Berichtsserver. Mit dem richtigen Authentifizierungstyp für Ihren Berichtsserver kann Ihr Unternehmen die den Anforderungen entsprechende Sicherheitsstufe erzielen. Weitere Informationen finden Sie unter [Authentication with the Report Server](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet auch Rollen und Berechtigungen, um den Benutzerzugriff auf Inhalte des Berichtsserverkatalogs (d.h. wer worauf und wie zugreifen kann) zu steuern. Weitere Informationen finden Sie unter [Rollen und Berechtigungen &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibungen|Links|  
|-----------------------|-----------|  
|Konfigurieren Sie zum Sichern von Clientverbindungen mit dem Berichtsserver die Transport Layer Security (TLS), früher als Secure Sockets Layer (SSL) bezeichnet.|[Konfigurieren von TLS-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
