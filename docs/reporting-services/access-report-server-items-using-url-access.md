---
title: Zugreifen auf Berichtsserverelemente über den URL-Zugriff | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie in einer Berichtsserver-Datenbank oder auf einer SharePoint-Website unter Verwendung von „rs:Command=Value“ auf Katalogelemente mit unterschiedlichen Typen zugreifen.
ms.date: 05/08/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9d415b9e263841757e7557e30cf3beb80e5afaa0
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246374"
---
# <a name="access-report-server-items-using-url-access"></a>Zugreifen auf Berichtsserverelemente über den URL-Zugriff
  In diesem Artikel wird beschrieben, wie Sie in einer Berichtsserver-Datenbank oder auf einer SharePoint-Website unter Verwendung von *rs:Command*=*Value* auf Katalogelemente mit unterschiedlichen Typen zugreifen. Es ist nicht erforderlich, diese Parameterzeichenfolge tatsächlich hinzuzufügen. Wenn Sie sie weglassen, wertet der Berichtsserver den Elementtyp aus und wählt den entsprechenden Parameterwert automatisch aus. Durch die Verwendung der *rs:Command*=*Value* -Zeichenfolge in der URL verbessert sich jedoch die Leistung des Berichtsservers.  
  
 Beachten Sie in den Beispielen unten die `_vti_bin` -Proxysyntax. Weitere Informationen zum Verwenden der Proxysyntax finden Sie unter [URL Access Parameter Reference](../reporting-services/url-access-parameter-reference.md).  

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.
  
## <a name="access-a-report"></a>Zugreifen auf einen Bericht  
 Verwenden Sie den *rs:Command*=*Render* -Parameter, um einen Bericht im Browser anzuzeigen. Beispiel:  
  
 - **Nativ** `https://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

 - **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Es ist wichtig, dass die URL die `_vti_bin` -Proxysyntax zur Weiterleitung der Anforderung über SharePoint sowie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -HTTP-Proxy enthält. Durch den Proxy wird der HTTP-Anforderung Kontext hinzugefügt. Dieser ist erforderlich, damit der Bericht auf Berichtsservern im SharePoint-Modus ordnungsgemäß ausgeführt wird.  

::: moniker-end
  
## <a name="access-a-resource"></a>Zugreifen auf eine Ressource  
 Verwenden Sie den *rs:Command*=*GetResourceContents* -Parameter, um auf eine Ressource zuzugreifen. Wenn die Ressource, z.B. ein Bild, mit dem Browser kompatibel ist, wird sie im Browser geöffnet. Andernfalls werden Sie aufgefordert, die Datei oder Ressource zu öffnen oder auf dem Datenträger zu speichern.  
  
 **Nativ** `https://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  

::: moniker-end
  
## <a name="access-a-data-source"></a>Zugreifen auf eine Datenquelle  
 Verwenden Sie den Parameter *rs:Command*=*GetDataSourceContents* , um auf eine Datenquelle zuzugreifen. Wenn Ihr Browser XML unterstützt, wird die Datenquellendefinition angezeigt, wenn Sie ein für die Datenquelle authentifizierter Benutzer mit der Berechtigung **Read Contents** sind. Beispiel:  
  
 **Nativ** `https://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 Die XML-Struktur kann Ähnlichkeit mit folgendem Beispiel haben:  

::: moniker-end
  
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
  
 Die Verbindungszeichenfolge wird auf Grundlage der **SecureConnectionLevel** -Einstellung des Berichtsservers zurückgegeben. Weitere Informationen zur **SecureConnectionLevel** -Einstellung finden Sie unter [Using Secure Web Service Methods](../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Zugreifen auf den Inhalt eines Ordners  
 Verwenden Sie den *rs:Command*=*GetChildren* -Parameter, um auf den Inhalt eines Ordners zuzugreifen. Es wird eine generische Seite zur Ordnernavigation zurückgegeben, die Links zu den Unterordnern, Berichten, Datenquellen und Ressourcen im angeforderten Ordner enthält. Beispiel:  
  
 **Nativ** `https://myrshost/reportserver?/Sales&rs:Command=GetChildren`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rs:Command=GetChildren`  

::: moniker-end
  
 Die angezeigte Benutzeroberfläche hat Ähnlichkeit mit dem Verzeichnissuchmodus, der von [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS (Internet Information Server) verwendet wird. Die Versionsnummer, einschließlich der Buildnummer des Berichtsservers, wird ebenfalls unter der Ordnerliste angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md) 
