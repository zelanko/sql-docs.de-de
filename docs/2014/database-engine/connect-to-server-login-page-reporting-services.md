---
title: Verbinden mit SQL Server Reporting Services (Seite 'Anmeldung') | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttors.login.f1
helpviewer_keywords:
- Connect to Server dialog box, Reporting Services
ms.assetid: d312c740-19d7-4931-84a2-88b805ec8439
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7369e9d37e5f706786410f8e171c89c6c38287d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62808722"
---
# <a name="connect-to-server-login-page-reporting-services"></a>Verbinden mit SQL Server Reporting Services (Seite 'Anmeldung')
  Verwenden Sie diese Registerkarte, um die folgenden Optionen für Verbindungen mit [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Optionen  
 **Servertyp**  
 Wenn Sie einen Server über den Objekt-Explorer registrieren, wählen Sie den Typ des Servers aus, mit dem eine Verbindung hergestellt wird: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services oder Integration Services. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über „Registrierte Server“ registrieren, ist das Feld **Servertyp** schreibgeschützt, wobei der Feldeintrag mit dem in der Komponente „Registrierte Server“ angezeigten Servertyp übereinstimmt. Zum Registrieren eines anderen Servertyps wählen Sie auf der Symbolleiste "Registrierte Server" die Option [!INCLUDE[ssDE](../includes/ssde-md.md)], "Analysis Services", "Reporting Services" oder "Integration Services" aus. Anschließend können Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Welche Werte Sie eingeben müssen, hängt von dem Servermodus der Berichtsserverinstanz ab, mit der Sie eine Verbindung herstellen.  
  
 Wenn es sich um einen Berichtsserver handelt, der im einheitlichen Modus ausgeführt wird, geben Sie die Berichtsserverinstanz an, mit der eine Verbindung hergestellt werden soll. Wenn Sie die Standardinstanz verwenden, ist der Servername in der Regel der Name des Computers. Wenn Sie eine benannte Instanz installiert haben, fügen Sie den Namen der Instanz an den Servernamen im folgenden Format: \<Servername >\\< InstanceName\>. Reporting Services verwendet den umgekehrten Schrägstrich zur Trennung des Instanznamens.  
  
 Für einen Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie eine SharePoint-Site angeben. Sie können eine beliebige Site aus einer Sitesammlung angeben, die mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integriert ist. Die URL, die Sie bereitstellen, muss das HTTP oder HTTPS-Präfix enthalten. Um in Management Studio eine Verbindung mit der SharePoint-Site herstellen zu können, müssen Sie über Zugriffsberechtigungen für die SharePoint-Site verfügen. Die Ihnen zugewiesene Berechtigungsstufe bestimmt, welche Elemente Sie anzeigen und verwalten können. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).  
  
 **Authentifizierung**  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kann so konfiguriert werden, dass Windows-Authentifizierungsanforderungen oder Formularauthentifizierungsanforderungen angenommen werden, die von einer von Ihnen bereitgestellten benutzerdefinierten Authentifizierungserweiterung verarbeitet werden. Wählen Sie beim Herstellen einer Verbindung mit Reporting Services einen der folgenden Authentifizierungsmodi aus:  
  
 **Windows-Authentifizierungsmodus (Windows-Authentifizierung)**  
 Stellt die Verbindung zur Berichtsserverinstanz mithilfe der Anmeldeinformationen von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows her.  
  
 **Standardauthentifizierung**  
 Stellen Sie die Verbindung mit **Standardauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Standardauthentifizierung konfiguriert ist.  
  
 **Formularauthentifizierung**  
 Stellen Sie die Verbindung mit **Formularauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Formularauthentifizierung konfiguriert ist.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, der für die Verbindung verwendet werden soll. Diese Option ist nur verfügbar, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den Benutzernamen ein. Diese Option kann nur bearbeitet werden, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Kennwort speichern**  
 Speichert das eingegebene Kennwort. Diese Option wird nur angezeigt, wenn Sie auf **Optionen**klicken, und kann nur bearbeitet werden, wenn Sie für das Herstellen der Verbindung die **Standardauthentifizierung** oder die **Formularauthentifizierung**ausgewählt haben.  
  
 **Verbinden**  
 Stellt eine Verbindung zum ausgewählten Server her.  
  
 **Options**  
 Zeigt zusätzliche Serververbindungsoptionen an, z. B. zum Speichern des Kennworts.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Authentication with the Report Server (Authentifizierung mit dem Berichtsserver)](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
