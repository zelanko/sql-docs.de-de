---
title: Programmgesteuerter Zugriff auf den WMI-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 67bd266b-1484-4863-8152-060a993420a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84c8d4f9ed6eccbf7e58be46a9b84c53559a317d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63232418"
---
# <a name="accessing-the-wmi-provider-programmatically"></a>Programmgesteuerter Zugriff auf den WMI-Anbieter
  Dieses Thema ist noch nicht abgeschlossen.  
  
## <a name="wmi-provider-overview"></a>Übersicht über WMI-Anbieter  
 Der Namespace, mit dem die Informationen zu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in den in diesem Thema gezeigten Codebeispielen abgerufen werden, ist der **System.Management**-Namespace, der in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] gefunden wurde. Der **System.Management**-Namespace enthält mehrere verwalteter Codeklassen, über die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Anwendungen auf Verwaltungsdaten zugreifen und diese bearbeiten können. Weitere Informationen zur Verwendung der Reporting Services-WMI-Klassen mit dem **System.Management**-Namespace finden Sie unter „Zugriff auf Verwaltungsinformationen mit System.Management“ im [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="finding-a-report-server-instance"></a>Suchen einer Berichtsserverinstanz  
 Die bevorzugte Art der Suche nach Informationen auf Ihren Berichtsserverinstallationen besteht im Durchlaufen der WMI-Instanzenauflistung. Im nachstehenden Beispiel sehen Sie, wie Eigenschaften auf jeder Berichtsserverinstanz gesucht werden: Es wird eine Auflistung erstellt, die zum Anzeigen der Eigenschaften immer wieder durchlaufen wird.  
  
```vb  
Imports System  
Imports System.Management  
Imports System.IO  
  
Module Module1  
    Sub Main()  
        Const WmiNamespace As String = "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin"  
        Const WmiRSClass As String = _  
           "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting"  
  
        Dim serverClass As ManagementClass  
        Dim scope As ManagementScope  
        scope = New ManagementScope(WmiNamespace)  
        'Connect to the Reporting Services namespace.  
        scope.Connect()  
  
        'Create the server class.  
        serverClass = New ManagementClass(WmiRSClass)  
        'Connect to the management object.  
        serverClass.Get()  
        If serverClass Is Nothing Then Throw New Exception("No class found")  
  
        'Loop through the instances of the server class.  
        Dim instances As ManagementObjectCollection = serverClass.GetInstances()  
        Dim instance As ManagementObject  
        For Each instance In instances  
            Console.Out.WriteLine("Instance Detected")  
            Dim instProps As PropertyDataCollection = instance.Properties  
            Dim prop As PropertyData  
            For Each prop In instProps  
                Dim name As String = prop.Name  
                Dim val As Object = prop.Value  
                Console.Out.Write("Property Name: " + name)  
                If val Is Nothing Then  
                    Console.Out.WriteLine("     Value: <null>")  
                Else  
                    Console.Out.WriteLine("     Value: " + val.ToString())  
                End If  
            Next  
        Next  
  
        Console.WriteLine("--- Press any key ---")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Management;  
using System.IO;  
[assembly: CLSCompliant(true)]  
  
class Class1  
{  
    [STAThread]  
    static void Main(string[] args)  
    {  
        const string WmiNamespace = @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin";  
        const string WmiRSClass =  
          @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting";  
        ManagementClass serverClass;  
        ManagementScope scope;  
        scope = new ManagementScope(WmiNamespace);  
  
        // Connect to the Reporting Services namespace.  
        scope.Connect();  
        // Create the server class.  
        serverClass = new ManagementClass(WmiRSClass);  
        // Connect to the management object.  
        serverClass.Get();  
        if (serverClass == null)  
            throw new Exception("No class found");  
  
        // Loop through the instances of the server class.  
        ManagementObjectCollection instances = serverClass.GetInstances();  
  
        foreach (ManagementObject instance in instances)  
        {  
            Console.Out.WriteLine("Instance Detected");  
            PropertyDataCollection instProps = instance.Properties;  
            foreach (PropertyData prop in instProps)  
            {  
                string name = prop.Name;  
                object val = prop.Value;  
                Console.Out.Write("Property Name: " + name);  
                if (val != null)  
                    Console.Out.WriteLine("     Value: " + val.ToString());  
                else  
                    Console.Out.WriteLine("     Value: <null>");  
            }  
        }  
        Console.WriteLine("\n--- Press any key ---");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf den Reporting Services WMI-Anbieter](tools/access-the-reporting-services-wmi-provider.md)   
 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)  
  
  
