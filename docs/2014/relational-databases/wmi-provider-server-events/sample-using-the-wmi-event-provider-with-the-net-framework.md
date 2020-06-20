---
title: 'Beispiel: Verwenden des WMI-Ereignis Anbieters mit dem .NET Framework | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Server Events, samples
- sample applications [WMI]
- managed code [WMI]
ms.assetid: 3d7aa7e9-0bb3-4a5b-9a3c-047f3240a6f8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c34922286d38e422cfd9667b64adac443e6a1c38
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059640"
---
# <a name="sample-using-the-wmi-event-provider-with-the-net-framework"></a>Beispiel: Verwenden des WMI-Ereignisanbieters mit .NET Framework
  Im folgenden Beispiel wird eine Anwendung in C# erstellt, die mit dem WMI-Ereignisanbieter Ereignisdaten für alle DDL-Ereignisse (Data Definition Language, Datendefinitionssprache) zurückgibt, die in der Standardinstallation einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz auftreten.  
  
## <a name="example"></a>Beispiel  
 Das Beispiel wird mit der folgenden Befehlszeile kompiliert:  
  
```  
set compiler_path=C:\WINNT\Microsoft.NET\Framework\v2.0.50110  
  
%compiler_path%\csc %1  
```  
  
```  
using System;  
using System.Management;  
  
class SQLWEPExample   
{  
    public static void Main(string[] args)  
    {  
        string query =  @"SELECT * FROM DDL_EVENTS " ;  
        // Default namespace for default instance of SQL Server   
        string managementPath =  
            @"\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER";  
        ManagementEventWatcher  watcher =   
            new ManagementEventWatcher(new WqlEventQuery (query));  
        ManagementScope scope = new ManagementScope (managementPath);  
        scope.Connect();  
        watcher.Scope = scope;  
        Console.WriteLine("Watching...");  
        while (true)  
        {  
            ManagementBaseObject obj = watcher.WaitForNextEvent();  
            Console.WriteLine("Event!");  
            foreach (PropertyData data in obj.Properties)  
            {  
                Console.Write("{0}:", data.Name);  
                if (data.Value == null)  
                {  
                    Console.WriteLine("<null>");  
                }  
                else  
                {  
                    Console.WriteLine(data.Value.ToString());  
                }  
            }  
            Console.WriteLine("-----");  
            Console.WriteLine();  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Serverereignisse](wmi-provider-for-server-events-concepts.md)  
  
  
