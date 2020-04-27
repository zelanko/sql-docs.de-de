---
title: Formatieren einer Reporting Services-Skriptdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df4585dfa4b1e45b2de9d396a59dcbf132b1a505
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100251"
---
# <a name="format-a-reporting-services-script-file"></a>Formatieren einer Reporting Services-Skriptdatei
  Bei einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skript handelt es sich um eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET-Codedatei, die für einen auf WSDL (Web Service Description Language) basierenden Proxy geschrieben wird und die Reporting Services-SOAP-API definiert. Eine Skriptdatei wird als Unicode- oder UTF-8-Textdatei mit der Erweiterung RSS gespeichert.  
  
 Die Skriptdatei fungiert als [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Modul und kann benutzerdefinierte Prozeduren und Modulebenenvariablen enthalten. Damit die Skriptdatei erfolgreich ausgeführt werden kann, muss sie eine Main-Prozedur enthalten. Die Main-Prozedur ist die erste Prozedur, auf die bei der Ausführung der Skriptdatei zugegriffen wird. In der Main-Prozedur können Sie Webdienstvorgänge hinzufügen und benutzerdefinierte Unterprozeduren ausführen. Im folgenden Code wird eine Main-Prozedur erstellt:  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 Von der Skriptumgebung wird automatisch eine Verbindung mit dem Berichtsserver hergestellt, die Webproxyklasse erstellt und eine Verweisvariable (*rs*) für das Webdienstproxyobjekt generiert. In den einzelnen von Ihnen erstellten Anweisungen muss nur auf die *rs* -Modulebenenvariable verwiesen werden, um beliebige der in der Webdienstbibliothek verfügbaren Webdienstvorgänge auszuführen. Mit dem folgenden [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Code wird die Webdienstmethode <xref:ReportService2010.ReportingService2010.ListChildren%2A> innerhalb einer Skriptdatei aufgerufen:  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  Benutzeranmeldeinformationen werden von der Skriptumgebung verwaltet und durch Argumente für die Eingabeaufforderung mithilfe von RS.exe übergeben. Sie können zwar die *rs* -Variable verwenden, um die Authentifizierung des Webdiensts festzulegen, allerdings wird die Verwendung der Skriptumgebung empfohlen. Die Authentifizierung des Webdiensts in der Skriptdatei selbst ist nicht erforderlich. Weitere Informationen zum Authentifizieren der Skriptumgebung finden Sie unter [Hilfsprogramm RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md).  
  
 Es werden keine Namespaces innerhalb der Skriptdatei deklariert. Sie Skriptumgebung stellt Ihnen einige nützliche [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Namespaces zur Verfügung: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml** und **System.IO**.  
  
 Skriptbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver-Webdienst](../report-server-web-service/report-server-web-service.md)   
 [Technische Referenz (SSRS)](../technical-reference-ssrs.md)   
 [Hilfsprogramm RS.exe (SSRS)](rs-exe-utility-ssrs.md)  
  
  
