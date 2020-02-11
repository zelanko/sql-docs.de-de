---
title: Konfigurieren der benutzerdefinierten oder Formularauthentifizierung auf dem Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7602ce0ef0e75c3c2eb1ee5a5a47e3fe56b87f44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102135"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a>Konfiguration der benutzerdefinierten oder Formularauthentifizierung auf dem Berichtsserver
  Reporting Services stellt eine erweiterbare Architektur zur Verfügung, mit der Sie benutzerdefinierte oder formularbasierte Authentifizierungsmodule integrieren können. Möglicherweise ist es ratsam, eine benutzerdefinierte Authentifizierungserweiterung zu implementieren, wenn die Bereitstellungsanforderungen keine Windows-integrierte Sicherheit oder grundlegende Authentifizierung umfassen. Das häufigste Szenario für die Verwendung der benutzerdefinierten Authentifizierung ist eine Unterstützung des Internet- oder Extranetzugriffs auf eine Webanwendung. Durch das Ersetzen der standardmäßigen Windows-Authentifizierungserweiterung durch eine benutzerdefinierte Erweiterung können Sie besser steuern, wie externen Benutzern Zugriff auf den Berichtsserver gewährt wird.  
  
 In der Praxis erfordert das Bereitstellen einer benutzerdefinierten Authentifizierungserweiterung mehrere Schritte, darunter das Kopieren von Assemblys und Anwendungsdateien, das Bearbeiten von Konfigurationsdateien und das Testen. Dieses Thema konzentriert sich ganz auf die Authentifizierungseinstellungen, die Sie in den Konfigurationsdateien angeben.  
  
> [!NOTE]  
>  Zum Erstellen einer benutzerdefinierten Authentifizierungserweiterung sind benutzerdefinierter Code und Kenntnisse der [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Sicherheit erforderlich. Wenn Sie keine benutzerdefinierte Authentifizierungserweiterung erstellen möchten, können Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory-Gruppen und -Konten verwenden, aber Sie sollten den Rahmen einer Berichtsserverbereitstellung deutlich verringern. Weitere Informationen zur benutzerdefinierten Authentifizierung finden Sie unter [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).  
  
 Wenn Sie eine Formular- oder benutzerdefinierte Authentifizierungserweiterung in einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Umgebung verwenden möchten, die mit einem SharePoint-Produkt integriert ist, müssen Sie zusätzlich die SharePoint-Website für die Verwendung der von Ihnen gewählten Authentifizierungsmethode konfigurieren. Weitere Informationen über das Konfigurieren der Authentifizierung in SharePoint finden Sie unter [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a>So konfigurieren Sie einen Berichtsserver für die Verwendung der benutzerdefinierten Authentifizierung  
  
1.  Öffnen Sie RSReportServer.config in einem Text-Editor.  
  
2.  Suchen Sie `Authentication` nach <>.  
  
3.  Kopieren Sie die folgende XML-Struktur:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  Fügen Sie Sie über die vorhandenen Einträge für `Authentication` <> ein.  
  
     Beachten Sie, dass Sie `Custom` nicht mit anderen Authentifizierungstypen verwenden können.  
  
5.  Speichern Sie die Datei .  
  
6.  Öffnen Sie die Datei Web.config für den Berichtsserver. Standardmäßig befindet sich diese Datei unter "Programme\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer".  
  
7.  Suchen `authentication mode` und festlegen `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  Suchen Sie `identity impersonate`, und legen Sie dafür `False` fest.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. Öffnen Sie die Datei Web.config für den Berichts-Manager. Standardmäßig befindet sich diese Datei unter \Programme\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.  
  
10. Suchen `authentication mode` und festlegen `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. Suchen Sie `identity impersonate`, und legen Sie dafür `False` fest.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. Fügen Sie der Konfigurationsdatei die Elementstruktur `PassThroughCookies` hinzu. Weitere Informationen finden Sie unter [Konfigurieren des Berichts-Managers für die Übergabe von benutzerdefinierten Authentifizierungscookies](configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
13. Speichern Sie die Datei .  
  
14. Wenn Sie eine horizontal skalierte Bereitstellung konfiguriert haben, wiederholen Sie alle vorherigen Schritte für andere in der Bereitstellung vorhandene Berichtsserver.  
  
15. Starten Sie den Berichtsserver neu, um alle momentan geöffneten Sitzungen zu beenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren einer Sicherheits Erweiterung](../extensions/security-extension/implementing-a-security-extension.md)   
 [Authentifizierung mit dem Berichtsserver](authentication-with-the-report-server.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)   
 [Konfigurieren der Standard Authentifizierung auf dem Berichts Server](configure-basic-authentication-on-the-report-server.md)   
 [Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver](configure-windows-authentication-on-the-report-server.md)  
  
  
