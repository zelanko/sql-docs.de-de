---
title: Abrufen in Konsolenanwendungen
description: Dieser Artikel enthält ein Beispiel zur Verwendung von Abrufen, um in einer Konsolenanwendung auf den Abschluss der Ausführung eines asynchronen Befehls zu warten. Diese Technik eignet sich auch in Klassenbibliotheken oder anderen Anwendungen ohne Benutzeroberfläche.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 89bcaa6d6e92ccde2d1c151b493c26fe1279d89f
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896644"
---
# <a name="polling-in-console-applications"></a>Abrufen in Konsolenanwendungen

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Mithilfe von asynchronen Vorgängen in ADO.NET können Sie zeitaufwendige Datenbankvorgänge auf einem Thread initiieren, während andere Tasks auf einem weiteren Thread ausgeführt werden. In den meisten Szenarios erreichen Sie jedoch irgendwann einen Punkt, an dem die Anwendung angehalten werden sollte, bis der Datenbankvorgang beendet ist. Dann ist es hilfreich, den asynchronen Vorgang abzurufen, um zu ermitteln, ob der Vorgang abgeschlossen wurde.  
  
Dafür können Sie die Eigenschaft <xref:System.IAsyncResult.IsCompleted%2A> verwenden.  
  
## <a name="example"></a>Beispiel  
Mit der folgenden Konsolenanwendung werden Daten innerhalb der **AdventureWorks**-Beispieldatenbank unter Verwendung eines asynchronen Vorgangs aktualisiert. In diesem Beispiel wird eine WAITFOR-Anweisung in den Befehlstext eingefügt, um einen Prozess mit langer Laufzeit zu emulieren. Normalerweise ist es nicht wünschenswert, dass Befehle langsamer ausgeführt werden, aber in diesem Fall kann dadurch das asynchrone Verhalten besser veranschaulicht werden.  
  
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
