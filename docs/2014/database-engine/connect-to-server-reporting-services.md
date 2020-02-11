---
title: Verbindung mit Server herstellen (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41e0ca3ee7ccaa7bb57e5667092c0660e35c4c52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62808677"
---
# <a name="connect-to-server-reporting-services"></a>Verbindung mit Server herstellen (Reporting Services)
  Verwenden Sie dieses Dialogfeld, um Optionen für die Verbindung [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]mit anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über **Objekt-Explorer**registrieren, wählen Sie den Typ des Servers aus, [!INCLUDE[ssDE](../includes/ssde-md.md)]mit dem eine Verbindung hergestellt werden soll:, Analysis Services, Reporting Services oder Integration Services. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über **registrierte Server**registrieren, ist das Feld **Servertyp** schreibgeschützt und entspricht dem in der Komponente **registrierte Server** angezeigten Servertyp. Um einen anderen Servertyp zu registrieren, [!INCLUDE[ssDE](../includes/ssde-md.md)]wählen Sie auf der Symbolleiste **registrierte Server** die Option, Analysis Services, Reporting Services oder Integration Services aus, bevor Sie mit dem Registrieren eines neuen Servers beginnen.  
  
 **Servername**  
 Welche Werte Sie eingeben müssen, hängt von dem Servermodus der Berichtsserverinstanz ab, mit der Sie eine Verbindung herstellen.  
  
 Wenn es sich um einen Berichtsserver handelt, der im einheitlichen Modus ausgeführt wird, geben Sie die Berichtsserverinstanz an, mit der eine Verbindung hergestellt werden soll. Wenn Sie die Standardinstanz verwenden, ist der Servername in der Regel der Name des Computers. Wenn Sie eine benannte Instanz installiert haben, fügen Sie den Instanznamen im folgenden Format an den Server \<Namen an: Server \\ Name><instanceName\>. Reporting Services verwendet den umgekehrten Schrägstrich zur Trennung des Instanznamens.  
  
 Für einen Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie eine SharePoint-Site angeben. Sie können eine beliebige Site aus einer Sitesammlung angeben, die mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integriert ist. Die URL, die Sie bereitstellen, muss das HTTP oder HTTPS-Präfix enthalten. Um in Management Studio eine Verbindung mit der SharePoint-Site herstellen zu können, müssen Sie über Zugriffsberechtigungen für die SharePoint-Site verfügen. Die Ihnen zugewiesene Berechtigungsstufe bestimmt, welche Elemente Sie anzeigen und verwalten können. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).  
  
 **Authentifizierung**  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kann so konfiguriert werden, dass Windows-Authentifizierungsanforderungen oder Formularauthentifizierungsanforderungen angenommen werden, die von einer von Ihnen bereitgestellten benutzerdefinierten Authentifizierungserweiterung verarbeitet werden. Wählen Sie beim Herstellen einer Verbindung mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]einen der folgenden Authentifizierungsmodi aus:  
  
 **Windows-Authentifizierungsmodus (Windows-Authentifizierung)**  
 Stellt die Verbindung zur Berichtsserverinstanz mithilfe der Anmeldeinformationen von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows her.  
  
 **Standardauthentifizierung**  
 Stellen Sie die Verbindung mit **Standardauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Standardauthentifizierung konfiguriert ist.  
  
 **Formular Authentifizierung**  
 Stellen Sie die Verbindung mit **Formularauthentifizierung** her, wenn die Reporting Services-Installation für die Verwendung der Formularauthentifizierung konfiguriert ist.  
  
 **Benutzer Name**  
 Geben Sie den Benutzernamen ein, der für die Verbindung verwendet werden soll. Diese Option ist nur verfügbar, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den Benutzernamen ein, Diese Option kann nur bearbeitet werden, wenn Sie **Standardauthentifizierung** oder **Formularauthentifizierung**ausgewählt haben.  
  
 **Herstellen einer Verbindung**  
 Klicken Sie hier, um eine Verbindung mit dem oben ausgewählten Server herzustellen.  
  
 **Optionen**  
 Klicken Sie auf diese Schaltfläche, um zusätzliche Optionen für die Serververbindung anzuzeigen, z. B. zum Registrieren eines Servers oder zum Speichern des Kennworts.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Authentication with the Report Server (Authentifizierung mit dem Berichtsserver)](../reporting-services/security/authentication-with-the-report-server.md)  
  
  
