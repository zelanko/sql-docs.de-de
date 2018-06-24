---
title: Verbindung mit Server herstellen (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.connection.login.reportserver.f1
ms.assetid: ef81b658-8eb5-4636-ac81-eead10cc7b9f
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 500624fbf81bc4ffc98ed3342878c2bf811005d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049948"
---
# <a name="connect-to-server-reporting-services"></a>Verbindung mit Server herstellen (Reporting Services)
  Verwenden Sie dieses Dialogfeld, um Optionen für Verbindungen mit Computern mit [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über den **Objekt-Explorer**registrieren, wählen Sie den Typ des Servers aus, mit dem eine Verbindung hergestellt wird: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services oder Integration Services. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über **Registrierte Server**registrieren, ist das Feld **Servertyp** schreibgeschützt, wobei der Feldeintrag mit dem in der Komponente **Registrierte Server** angezeigten Servertyp übereinstimmt. Um einen anderen Servertyp zu registrieren, wählen Sie auf der Symbolleiste [!INCLUDE[ssDE](../includes/ssde-md.md)]Registrierte Server **die Option „** “, „Analysis Services“, „Reporting Services“ oder „Integration Services“ aus. Anschließend können Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Welche Werte Sie eingeben müssen, hängt von dem Servermodus der Berichtsserverinstanz ab, mit der Sie eine Verbindung herstellen.  
  
 Wenn es sich um einen Berichtsserver handelt, der im einheitlichen Modus ausgeführt wird, geben Sie die Berichtsserverinstanz an, mit der eine Verbindung hergestellt werden soll. Wenn Sie die Standardinstanz verwenden, ist der Servername in der Regel der Name des Computers. Wenn Sie eine benannte Instanz installiert haben, fügen Sie den Namen der Instanz auf den Servernamen im folgenden Format: \<Servername >\\< InstanceName\>. Reporting Services verwendet den umgekehrten Schrägstrich zur Trennung des Instanznamens.  
  
 Für einen Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie eine SharePoint-Site angeben. Sie können eine beliebige Site aus einer Sitesammlung angeben, die mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integriert ist. Die URL, die Sie bereitstellen, muss das HTTP oder HTTPS-Präfix enthalten. Um in Management Studio eine Verbindung mit der SharePoint-Site herstellen zu können, müssen Sie über Zugriffsberechtigungen für die SharePoint-Site verfügen. Die Ihnen zugewiesene Berechtigungsstufe bestimmt, welche Elemente Sie anzeigen und verwalten können. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md).  
  
 **Authentifizierung**  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kann so konfiguriert werden, dass Windows-Authentifizierungsanforderungen oder Formularauthentifizierungsanforderungen angenommen werden, die von einer von Ihnen bereitgestellten benutzerdefinierten Authentifizierungserweiterung verarbeitet werden. Wählen Sie beim Herstellen einer Verbindung mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]einen der folgenden Authentifizierungsmodi aus:  
  
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
  
 **Verbinden**  
 Klicken Sie hier, um eine Verbindung mit dem oben ausgewählten Server herzustellen.  
  
 **Optionen**  
 Klicken Sie auf diese Schaltfläche, um zusätzliche Optionen für die Serververbindung anzuzeigen, z. B. zum Registrieren eines Servers oder zum Speichern des Kennworts.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren Sie eine Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Authentication with the Report Server (Authentifizierung mit dem Berichtsserver)](../reporting-services/security/authentication-with-the-report-server.md)  
  
  