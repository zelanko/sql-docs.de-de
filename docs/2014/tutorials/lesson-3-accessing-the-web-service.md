---
title: 'Lektion 3: Zugreifen auf den Webdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
caps.latest.revision: 43
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9e5decf2f1d6c702b3bc3483ffb89bff9a2cd9f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230130"
---
# <a name="lesson-3-accessing-the-web-service"></a>Lektion 3: Zugreifen auf den Webdienst
  Nachdem Sie dem Projekt einen Verweis auf den Berichtsserver-Webdienst hinzugefügt haben, besteht der nächste Schritt darin, eine Instanz der Proxyklasse des Webdiensts zu erstellen. Auf die Methoden des Webdiensts kann durch Aufrufen der Methoden in der Proxyklasse zugegriffen werden. Wenn Ihre Anwendung diese Methoden aufruft, wird der Proxy Klasse vom generierten Code [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erfolgt die Kommunikation zwischen Ihrer Anwendung und dem Webdienst.  
  
 Erstellen Sie zunächst eine Instanz der Proxyklasse des Webdiensts <xref:ReportService2010.ReportingService2010>. Dann rufen Sie die <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode des Webdiensts mithilfe der Proxyklasse auf. Sie verwenden diesen Aufruf zum Abrufen des Namens und der Beschreibung eines der Beispielsberichte, Company Sales.  
  
> [!NOTE]  
>  Beim Zugreifen auf einen Webdienst, der unter [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] mit Advanced Services ausgeführt wird, müssen Sie "$SQLExpress" an den "ReportServer"-Pfad anfügen. Zum Beispiel:  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a>So greifen Sie auf den Webdienst zu  
  
1.  Zunächst müssen Sie der Datei Program.cs (Module1.vb in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) den Namespace hinzufügen, indem Sie der Codedatei eine `using`-Direktive (`Imports` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) hinzufügen. Wenn Sie diese Direktive verwenden, müssen die Typen im Namespace nicht vollqualifiziert sein.  
  
2.  Fügen Sie dazu den folgenden Code am Anfang der Codedatei ein:  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  Nachdem Sie die Namespacedirektive in die Codedatei eingegeben haben, geben Sie den folgenden Code in die Main-Methode Ihrer Konsolenanwendung ein. Stellen Sie sicher, dass Sie beim Festlegen der **Url** -Eigenschaft der Webdienstinstanz den Namen Ihres Servers ändern:  
  
    ```vb  
    Sub Main()  
       Dim rs As New ReportingService2010  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx"  
  
       Dim name As New [Property]  
       name.Name = "Name"  
  
       Dim description As New [Property]  
       description.Name = "Description"  
  
       Dim properties(1) As [Property]  
       properties(0) = name  
       properties(1) = description  
  
       Try  
          Dim returnProperties As [Property]() = rs.GetProperties( _  
             "/AdventureWorks 2012 Sample Reports/Company Sales 2012", properties)  
  
          Dim p As [Property]  
          For Each p In returnProperties  
              Console.WriteLine((p.Name + ": " + p.Value))  
          Next p  
  
       Catch e As Exception  
          Console.WriteLine(e.Message)  
       End Try  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
       ReportingService2010 rs = new ReportingService2010();  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx";  
  
       Property name = new Property();  
       name.Name = "Name";  
  
       Property description = new Property();  
       description.Name = "Description";  
  
       Property[] properties = new Property[2];  
       properties[0] = name;  
       properties[1] = description;  
  
       try  
       {  
          Property[] returnProperties = rs.GetProperties(  
          "/AdventureWorks 2012 Sample Reports/Company Sales 2012",properties);  
  
          foreach (Property p in returnProperties)  
          {  
             Console.WriteLine(p.Name + ": " + p.Value);  
          }  
       }  
  
       catch (Exception e)  
       {  
          Console.WriteLine(e.Message);  
       }  
    }  
    ```  
  
4.  Speichern Sie die Projektmappe.  
  
 Der Beispielcode für die exemplarische Vorgehensweise verwendet die <xref:ReportService2010.ReportingService2010.GetProperties%2A> -Methode der Webdienst für die Eigenschaften des Beispielberichts Company Sales 2012 abzurufen. Die <xref:ReportService2010.ReportingService2010.GetProperties%2A> Methode akzeptiert zwei Argumente: den Namen des Berichts für die abzurufenden Informationen und ein Array von **Property []** Objekten, das die Namen der Eigenschaften enthält, dessen Werte Sie abrufen möchten. Die Methode gibt auch ein Array von **Property[]** -Objekten zurück, die die Namen und Werte der Eigenschaften enthalten, die im Eigenschaftenargument angegeben sind.  
  
> [!NOTE]  
>  Wenn Sie ein leeres **Property[]** -Array für das Eigenschaftenargument angeben, werden alle verfügbaren Eigenschaften zurückgegeben.  
  
 Im vorherigen Beispiel verwendet der Code die <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode, um den Namen und die Beschreibung des Beispielberichts Company Sales 2012 zurückzugeben. Im Code wird dann eine `foreach`-Schleife verwendet, um die Eigenschaften und Werte auf die Konsole zu schreiben.  
  
 Weitere Informationen zum Erstellen und verwenden eine Proxyklasse für den Berichtsserver-Webdienst finden Sie unter [Erstellen des Webdienstproxys](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lektion 4: Ausführen der Anwendung &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Zugreifen auf die Berichtsserver-Webdienst mit Visual Basic oder Visual C#&#35; &#40;SSRS-Tutorial&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
