---
title: Zugreifen auf Berichtsserverelemente über URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a345cd609c4cfd79f9e93a2b63e71bbddde36ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233568"
---
# <a name="access-report-server-items-using-url-access"></a>Zugreifen auf Berichtsserverelemente über URL-Zugriff
  Diesem Thema wird beschrieben, wie auf Katalogelemente mit unterschiedlichen Typen in einen Bericht zugreifen Serverdaten basieren oder in einer SharePoint-Website unter Verwendung *Rs: Command*=*Wert*.  
  
 Es ist nicht notwendig, diese Parameterzeichenfolge hinzuzufügen. Wenn Sie weggelassen wird, wird der Berichtsserver den Elementtyp ergibt und wählt den entsprechenden Parameterwert automatisch. Verwenden Sie jedoch die *Rs: Command*=*Wert* -Zeichenfolge in der URL verbessert die Leistung des Berichtsservers.  
  
 Beachten Sie die `_vti_bin` proxysyntax in den folgenden Beispielen. Weitere Informationen zum Verwenden der proxysyntax finden Sie unter [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Zugreifen auf einen Bericht  
 Verwenden Sie zum Anzeigen eines Berichts im Browser die *Rs: Command*=*Rendern* Parameter. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Es ist wichtig, dass die URL der `_vti_bin` proxysyntax zur Weiterleitung der Anforderung über SharePoint und die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP-Proxy. Der Proxy hinzugefügt. der HTTP-Anforderung Kontext, der erforderlich ist, um die ordnungsgemäße Ausführung des Berichts für Berichtsserver im SharePoint-Modus zu gewährleisten.  
  
## <a name="access-a-resource"></a>Zugreifen auf eine Ressource  
 Um eine Ressource zuzugreifen, verwenden die *Rs: Command*=*GetResourceContents* Parameter. Wenn die Ressource mit dem Browser, z. B. ein Bild, kompatibel ist, wird es im Browser geöffnet. Andernfalls werden Sie aufgefordert, zum Öffnen oder speichern die Datei oder Ressource, auf dem Datenträger.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Zugriff auf eine Datenquelle  
 Um eine Datenquelle zuzugreifen, verwenden die *Rs: Command*=*GetDataSourceContents* Parameter. Wenn Ihr Browser XML unterstützt, wird die Datenquellendefinition angezeigt, wenn Sie ein authentifizierter Benutzer mit sind `Read Contents` -Berechtigung für die Datenquelle. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 Die XML-Struktur sieht wie im folgenden Beispiel aus:  
  
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
  
 Wird zurückgegeben, die Verbindungszeichenfolge auf Grundlage der **SecureConnectionLevel** des Berichtsservers festlegen. Weitere Informationen zu den **SecureConnectionLevel** finden Sie unter [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Zugriff auf den Inhalt eines Ordners  
 Um den Inhalt eines Ordners zuzugreifen, verwenden die *Rs: Command*=*GetChildren* Parameter. Eine generische Ordnernavigation-Seite zurückgegeben, die Links zu den Unterordnern, Berichten, Datenquellen und Ressourcen im angeforderten Ordner enthält. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Die Benutzeroberfläche, die Sie sehen, ähnelt dem verzeichnissuchmodus, die von verwendet [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS). Die Versionsnummer, einschließlich der Buildnummer des Berichtsservers wird auch unter der Ordnerliste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
  
  
