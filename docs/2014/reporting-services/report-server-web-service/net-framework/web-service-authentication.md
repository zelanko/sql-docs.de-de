---
title: Webdienstauthentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aaccc593ea7e4baece132b759ca920018cdbe4b4
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60157416"
---
# <a name="web-service-authentication"></a>Webdienstauthentifizierung
  Sie können entweder die Windows-Authentifizierung oder die Standardauthentifizierung verwenden, um an den Berichtsserver-Webdienst gerichtete Aufrufe zu authentifizieren. Jeder Client, der SOAP-Anforderungen an den Berichtsserver richtet, muss den Clientteil eines der unterstützten Authentifizierungsprotokolle implementieren. Wenn Sie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verwenden, können Sie die Authentifizierung mithilfe von HTTP-Klassen mit verwaltetem Code implementieren. Mithilfe von APIs können Sie die Authentifizierungsdaten problemlos zusammen mit den SOAP-Anforderungen senden.  
  
 Wenn Sie die entsprechenden Anmeldeinformationen nicht haben, bevor Sie einen Aufruf an den Berichtsserver-Webdienst richten, schlägt der Aufruf fehl. Sie können die Anmeldeinformationen zur Laufzeit an den Webdienst übergeben, indem Sie die **Credentials**-Eigenschaft des clientseitigen Objekts festlegen, das den XML-Webdienst darstellt, bevor Sie seine Methoden aufrufen.  
  
 Die folgenden Abschnitte enthalten Beispielcode, der die Anmeldeinformationen mithilfe von [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sendet.  
  
## <a name="windows-authentication"></a>Windows-Authentifizierung  
 Folgender Code übergibt die Windows-Anmeldeinformationen an den Webdienst.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Standardauthentifizierung  
 Folgender Code übergibt die Standardanmeldeinformationen an den Webdienst.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 Die Anmeldeinformationen müssen jedoch festgelegt sein, bevor Sie eine der Methoden des Berichtsserver-Webdiensts aufrufen. Wenn Sie die Anmeldeinformationen nicht festlegen, wird den Fehlercode einem HTTP 401-Fehler: Zugriff verweigert. Sie müssen den Dienst vor der Verwendung authentifizieren, aber wenn Sie die Anmeldeinformationen festgelegt haben, müssen Sie diese nicht nochmals festlegen, solange Sie weiterhin dieselbe Dienstvariable verwenden (z. B. *rs*).  
  
## <a name="custom-authentication"></a>Benutzerdefinierte Authentifizierung  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthält eine Programmierungs-API, mit denen Entwickler benutzerdefinierte Authentifizierungserweiterungen, so genannte Sicherheitserweiterungen, entwerfen und entwickeln können. Weitere Informationen finden Sie unter [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Report Server Web Service (Report Server-Webdienst)](../report-server-web-service.md)  
  
  
