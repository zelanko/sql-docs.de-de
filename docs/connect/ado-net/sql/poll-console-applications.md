---
title: Abrufen in Konsolenanwendungen
description: Enthält ein Beispiel für die Verwendung von Abruf, um auf den Abschluss einer asynchronen Befehlsausführung aus einer Konsolenanwendung zu warten. Diese Technik ist auch in einer Klassenbibliothek oder einer anderen Anwendung ohne Benutzeroberfläche gültig.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: e8dc5597743a277b53f36d0bfb1487a12cbd80d9
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452099"
---
# <a name="polling-in-console-applications"></a>Abrufen in Konsolenanwendungen

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Mit asynchronen Vorgängen in ADO.net können Sie zeitaufwändige Daten Bank Vorgänge in einem Thread initiieren, während Sie andere Tasks in einem anderen Thread ausführen. In den meisten Szenarios erreichen Sie jedoch irgendwann einen Punkt, an dem die Anwendung nicht fortgesetzt werden sollte, bis der Daten Bank Vorgang beendet ist. In solchen Fällen ist es hilfreich, den asynchronen Vorgang abzufragen, um zu bestimmen, ob der Vorgang abgeschlossen wurde oder nicht.  
  
Sie können die <xref:System.IAsyncResult.IsCompleted%2A>-Eigenschaft verwenden, um herauszufinden, ob der Vorgang abgeschlossen wurde.  
  
## <a name="example"></a>Beispiel  
Mit der folgenden Konsolenanwendung werden Daten innerhalb der **AdventureWorks**-Beispieldatenbank unter Verwendung eines asynchronen Vorgangs aktualisiert. Um einen Prozess mit langer Laufzeit zu emulieren, fügt dieses Beispiel eine WAITFOR-Anweisung in den Befehls Text ein. Normalerweise würden Sie nicht versuchen, die Befehle langsamer auszuführen, aber dies ist in diesem Fall einfacher, um das asynchrone Verhalten zu veranschaulichen.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
    [STAThread]  
    static void Main()  
    {  
        // The WAITFOR statement simply adds enough time to   
        // prove the asynchronous nature of the command.  
  
        string commandText =  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint + 1 " +  
          "WHERE ReorderPoint Is Not Null;" +  
          "WAITFOR DELAY '0:0:3';" +  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint - 1 " +  
          "WHERE ReorderPoint Is Not Null";  
  
        RunCommandAsynchronously(  
            commandText, GetConnectionString());  
  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  
    private static void RunCommandAsynchronously(  
      string commandText, string connectionString)  
    {  
        // Given command text and connection string, asynchronously  
        // execute the specified command against the connection.   
        // For this example, the code displays an indicator as it's   
        // working, verifying the asynchronous behavior.   
        using (SqlConnection connection =  
          new SqlConnection(connectionString))  
        {  
            try  
            {  
                int count = 0;  
                SqlCommand command =   
                    new SqlCommand(commandText, connection);  
                connection.Open();  
  
                IAsyncResult result =   
                    command.BeginExecuteNonQuery();  
                while (!result.IsCompleted)  
                {  
                    Console.WriteLine(  
                                    "Waiting ({0})", count++);  
                    // Wait for 1/10 second, so the counter  
                    // doesn't consume all available   
                    // resources on the main thread.  
                    System.Threading.Thread.Sleep(100);  
                }  
                Console.WriteLine(  
                    "Command complete. Affected {0} rows.",  
                command.EndExecuteNonQuery(result));  
            }  
            catch (SqlException ex)  
            {  
                Console.WriteLine("Error ({0}): {1}",   
                    ex.Number, ex.Message);  
            }  
            catch (InvalidOperationException ex)  
            {  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
            catch (Exception ex)  
            {  
                // You might want to pass these errors  
                // back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
        }  
    }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
  
        // If you have not included "Asynchronous Processing=true"  
        // in the connection string, the command will not be able  
        // to execute asynchronously.  
        return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks; " +   
        "Asynchronous Processing=true";  
    }  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Asynchrone Vorgänge](asynchronous-operations.md)
