---
title: Zugreifen auf Berichtsserverelemente über den URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e7184a0a5aa72ea7fe4ff681103044f2791bdf33
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227084"
---
# <a name="access-report-server-items-using-url-access"></a>Zugreifen auf Berichtsserverelemente über den URL-Zugriff
  In diesem Thema wird beschrieben, wie Sie in einer Berichtsserver-Datenbank oder auf einer SharePoint-Website unter Verwendung von *rs:Befehl*=*Wert*auf Katalogelemente mit unterschiedlichen Typen zugreifen.  
  
 Es ist nicht erforderlich, diese Parameterzeichenfolge hinzuzufügen. Wenn Sie sie weglassen, wertet der Berichtsserver den Elementtyp aus und wählt den entsprechenden Parameterwert automatisch aus. Durch die Verwendung der *rs:Command*=*Value* -Zeichenfolge in der URL verbessert sich jedoch die Leistung des Berichtsservers.  
  
 Beachten Sie in den Beispielen unten die `_vti_bin` -Proxysyntax. Weitere Informationen zum Verwenden der proxysyntax finden Sie unter [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Zugreifen auf einen Bericht  
 Verwenden Sie den *rs:Command*=*Render* -Parameter, um einen Bericht im Browser anzuzeigen. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Es ist wichtig, dass die URL die `_vti_bin` -Proxysyntax zur Weiterleitung der Anforderung über SharePoint sowie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -HTTP-Proxy enthält. Durch den Proxy wird der HTTP-Anforderung Kontext hinzugefügt. Dieser ist erforderlich, damit der Bericht auf Berichtsservern im SharePoint-Modus ordnungsgemäß ausgeführt wird.  
  
## <a name="access-a-resource"></a>Zugreifen auf eine Ressource  
 Verwenden Sie den *rs:Command*=*GetResourceContents* -Parameter, um auf eine Ressource zuzugreifen. Wenn die Ressource, z.B. ein Bild, mit dem Browser kompatibel ist, wird sie im Browser geöffnet. Andernfalls werden Sie aufgefordert, die Datei oder Ressource zu öffnen oder auf dem Datenträger zu speichern.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Zugreifen auf eine Datenquelle  
 Verwenden Sie den Parameter *rs:Command*=*GetDataSourceContents* , um auf eine Datenquelle zuzugreifen. Wenn Ihr Browser XML unterstützt, wird die Datenquellendefinition angezeigt, wenn Sie ein für die Datenquelle authentifizierter Benutzer mit der Berechtigung `Read Contents` sind. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 Die XML-Struktur kann Ähnlichkeit mit folgendem Beispiel haben:  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 Die Verbindungszeichenfolge wird auf Grundlage der **SecureConnectionLevel** -Einstellung des Berichtsservers zurückgegeben. Weitere Informationen zu den **SecureConnectionLevel** finden Sie unter [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Zugreifen auf den Inhalt eines Ordners  
 Verwenden Sie den *rs:Command*=*GetChildren* -Parameter, um auf den Inhalt eines Ordners zuzugreifen. Es wird eine generische Seite zur Ordnernavigation zurückgegeben, die Links zu den Unterordnern, Berichten, Datenquellen und Ressourcen im angeforderten Ordner enthält. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Die angezeigte Benutzeroberfläche hat Ähnlichkeit mit dem Verzeichnissuchmodus, der von [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS (Internet Information Server) verwendet wird. Die Versionsnummer, einschließlich der Buildnummer des Berichtsservers, wird ebenfalls unter der Ordnerliste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
  
