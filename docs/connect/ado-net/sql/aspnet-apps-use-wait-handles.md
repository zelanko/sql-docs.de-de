---
title: Verwenden von Wait-Handles in ASP.NET-Anwendungen
description: Enthält ein Beispiel, das veranschaulicht, wie mehrere gleichzeitige Befehle auf einer ASP.NET-Seite ausgeführt werden können, wobei Wait-Handles verwendet werden, um den Vorgang nach Ausführung aller Befehle zu verwalten.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: f588597a-49de-4206-8463-4ef377e112ff
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 42d5c395526ff79e24243392bb3dbfa302c8a9e7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897075"
---
# <a name="aspnet-applications-using-wait-handles"></a>Verwenden von Wait-Handles in ASP.NET-Anwendungen

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Die Rückruf- und Abfragemodelle für die Abwicklung asynchroner Vorgänge sind nützlich, wenn Ihre Anwendung jeweils nur einen asynchronen Vorgang verarbeitet. Die Wait-Modelle bieten eine flexiblere Möglichkeit zur Verarbeitung mehrerer asynchroner Vorgänge. Es gibt zwei Wait-Modelle, benannt nach den zur Implementierung verwendeten <xref:System.Threading.WaitHandle>-Methoden: das Wait (Any)-Modell und das Wait (All)-Modell.  
  
Um eines der beiden Wait-Modelle verwenden zu können, müssen Sie die <xref:System.IAsyncResult.AsyncWaitHandle%2A>-Eigenschaft des <xref:System.IAsyncResult>-Objekts verwenden, das von den Methoden <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> oder <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> zurückgegeben wird. Die Methoden <xref:System.Threading.WaitHandle.WaitAny%2A> und <xref:System.Threading.WaitHandle.WaitAll%2A> erfordern beide, dass Sie die <xref:System.Threading.WaitHandle>-Objekte gruppiert in einem Array als Argument senden.  
  
Beide Wait-Methoden überwachen die asynchronen Vorgänge und warten auf den Abschluss. Die <xref:System.Threading.WaitHandle.WaitAny%2A>-Methode wartet auf die Beendigung oder das Timeout einer der Operationen. Wenn bekannt ist, dass eine bestimmte Operation abgeschlossen ist, können Sie die Ergebnisse verarbeiten und dann weiter auf die Beendigung oder das Timeout der nächsten Operation warten. Die <xref:System.Threading.WaitHandle.WaitAll%2A>-Methode wartet vor dem Fortfahren auf die Beendigung oder das Timeout aller Prozesse im Array der <xref:System.Threading.WaitHandle>-Instanzen.  
  
Der Vorteil der Wait-Modelle ist am auffälligsten, wenn Sie mehrere Vorgänge von einiger Länge auf verschiedenen Servern ausführen müssen oder wenn Ihr Server leistungsfähig genug ist, um alle Abfragen gleichzeitig zu verarbeiten. In den hier vorgestellten Beispielen emulieren drei Abfragen lange Prozesse, indem unterschiedlich lange WAITFOR-Befehle zu folgenlosen SELECT-Abfragen hinzugefügt werden.  
  
## <a name="example-wait-any-model"></a>Beispiel: Wait (Any)-Modell  
Das folgende Beispiel veranschaulicht das Wait (Any)-Modell. Nach dem Start von drei asynchronen Prozessen wird die <xref:System.Threading.WaitHandle.WaitAny%2A>-Methode aufgerufen, um auf den Abschluss eines beliebigen dieser Prozesse zu warten. Am Ende jedes Prozesses wird die <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A>-Methode aufgerufen und das resultierende <xref:Microsoft.Data.SqlClient.SqlDataReader>-Objekt gelesen. An dieser Stelle würde eine reale Anwendung wahrscheinlich <xref:Microsoft.Data.SqlClient.SqlDataReader> verwenden, um einen Teil der Seite aufzufüllen. Bei diesem einfachen Beispiel wird die Zeit, zu der der Prozess abgeschlossen wurde, in ein Textfeld eingefügt, das zum Prozess gehört. Die Zeitangaben in den Textfeldern verdeutlichen zusammengenommen Folgendes: Bei jeder Beendigung eines Prozesses wird Code ausgeführt.  
  
Um dieses Beispiel einzurichten, erstellen Sie ein neues ASP.NET-Websiteprojekt. Platzieren Sie ein <xref:System.Web.UI.WebControls.Button>-Steuerelement und vier <xref:System.Web.UI.WebControls.TextBox>-Steuerelemente auf der Seite (wobei der Standardname für jedes Steuerelement übernommen wird).  
  
Fügen Sie der Klasse des Formulars den folgenden Code hinzu, wobei Sie die Verbindungszeichenfolge entsprechend Ihrer Umgebung ändern müssen.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
     //  To avoid storing the connection string in your code,              
     //  you can retrieve it from a configuration file.   
     //  If you have not included "Asynchronous Processing=true"   
     //  in the connection string, the command will not be able  
     //  to execute asynchronously.  
{  
     return "Data Source=(local);Integrated Security=SSPI;" +  
          "Initial Catalog=AdventureWorks;" +  
          "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
     //  In a real-world application, you might be connecting to   
     //   three different servers or databases. For the example,  
     //   we connect to only one.  
  
     SqlConnection connection1 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection2 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection3 =   
          new SqlConnection(GetConnectionString());  
     //  To keep the example simple, all three asynchronous   
     //  processes select a row from the same table. WAITFOR  
     //  commands are used to emulate long-running processes  
     //  that complete after different periods of time.  
  
     string commandText1 = "WAITFOR DELAY '0:0:01';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText2 = "WAITFOR DELAY '0:0:05';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText3 = "WAITFOR DELAY '0:0:10';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     try  
          //  For each process, open a connection and begin   
          //  execution. Use the IAsyncResult object returned by   
          //  BeginExecuteReader to add a WaitHandle for the   
          //  process to the array.  
     {  
          connection1.Open();  
          SqlCommand command1 =  
               new SqlCommand(commandText1, connection1);  
          IAsyncResult result1 = command1.BeginExecuteReader();  
          WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
  
          connection2.Open();  
          SqlCommand command2 =  
               new SqlCommand(commandText2, connection2);  
          IAsyncResult result2 = command2.BeginExecuteReader();  
          WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
  
          connection3.Open();  
          SqlCommand command3 =  
               new SqlCommand(commandText3, connection3);  
          IAsyncResult result3 = command3.BeginExecuteReader();  
          WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
          WaitHandle[] waitHandles = {  
               waitHandle1, waitHandle2, waitHandle3  
          };  
  
          int index;  
          for (int countWaits = 0; countWaits <= 2; countWaits++)  
          {  
               //  WaitAny waits for any of the processes to   
               //  complete. The return value is either the index   
               //  of the array element whose process just   
               //  completed, or the WaitTimeout value.  
  
               index = WaitHandle.WaitAny(waitHandles,   
                    60000, false);  
               //  This example doesn't actually do anything with   
               //  the data returned by the processes, but the   
               //  code opens readers for each just to demonstrate       
               //  the concept.  
               //  Instead of using the returned data to fill the   
               //  controls on the page, the example adds the time  
               //  the process was completed to the corresponding  
               //  text box.  
  
               switch (index)  
               {  
                    case 0:  
                         SqlDataReader reader1;  
                         reader1 =   
                              command1.EndExecuteReader(result1);  
                         if (reader1.Read())  
                         {  
                           TextBox1.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader1.Close();  
                         break;  
                    case 1:  
                         SqlDataReader reader2;  
                         reader2 =   
                              command2.EndExecuteReader(result2);  
                         if (reader2.Read())  
                         {  
                           TextBox2.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader2.Close();  
                         break;  
                    case 2:  
                         SqlDataReader reader3;  
                         reader3 =   
                              command3.EndExecuteReader(result3);  
                         if (reader3.Read())  
                         {  
                           TextBox3.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader3.Close();  
                         break;  
                    case WaitHandle.WaitTimeout:  
                         throw new Exception("Timeout");  
                         break;  
               }  
          }  
     }  
     catch (Exception ex)  
     {  
          TextBox4.Text = ex.ToString();  
     }  
     connection1.Close();  
     connection2.Close();  
     connection3.Close();  
}  
```  
  
## <a name="example-wait-all-model"></a>Beispiel: Wait (All)-Modell  
Das folgende Beispiel veranschaulicht das Wait (All)-Modell. Nachdem drei asynchrone Prozesse gestartet wurden, wird die <xref:System.Threading.WaitHandle.WaitAll%2A>-Methode aufgerufen, um auf den Abschluss oder das Timeout der Prozesse zu warten.  
  
Wie im Beispiel des Wait (Any)-Modells wird die Zeit, zu der der Prozess abgeschlossen ist, in ein Textfeld eingefügt, das zum Prozess gehört. Wiederum verdeutlichen die Zeitangaben in den Textfeldern Folgendes: Code, der auf die <xref:System.Threading.WaitHandle.WaitAny%2A>-Methode folgt, wird erst nach Beendigung aller Prozesse ausgeführt.  
  
Um dieses Beispiel einzurichten, erstellen Sie ein neues ASP.NET-Websiteprojekt. Platzieren Sie ein <xref:System.Web.UI.WebControls.Button>-Steuerelement und vier <xref:System.Web.UI.WebControls.TextBox>-Steuerelemente auf der Seite (wobei der Standardname für jedes Steuerelement übernommen wird).  
  
Fügen Sie der Klasse des Formulars den folgenden Code hinzu, wobei Sie die Verbindungszeichenfolge entsprechend Ihrer Umgebung ändern müssen.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
    //  To avoid storing the connection string in your code,              
    //  you can retrieve it from a configuration file.   
    //  If you have not included "Asynchronous Processing=true"   
    //  in the connection string, the command will not be able  
    //  to execute asynchronously.  
{  
    return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks;" +  
        "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
    //  In a real-world application, you might be connecting to   
    //   three different servers or databases. For the example,  
    //   we connect to only one.  
  
    SqlConnection connection1 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection2 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection3 =   
        new SqlConnection(GetConnectionString());  
    //  To keep the example simple, all three asynchronous   
    //  processes execute UPDATE queries that result in  
      //  no change to the data. WAITFOR  
    //  commands are used to emulate long-running processes  
    //  that complete after different periods of time.  
  
    string commandText1 =   
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint + 1 " +  
        "WHERE ReorderPoint Is Not Null;" +  
        "WAITFOR DELAY '0:0:01';" +  
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint - 1 " +  
        "WHERE ReorderPoint Is Not Null";  
  
    string commandText2 =   
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint + 1 " +  
      "WHERE ReorderPoint Is Not Null;" +  
      "WAITFOR DELAY '0:0:05';" +  
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint - 1 " +  
      "WHERE ReorderPoint Is Not Null";  
  
    string commandText3 =  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint + 1 " +  
       "WHERE ReorderPoint Is Not Null;" +  
       "WAITFOR DELAY '0:0:10';" +  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint - 1 " +  
       "WHERE ReorderPoint Is Not Null";  
    try  
        //  For each process, open a connection and begin   
        //  execution. Use the IAsyncResult object returned by   
        //  BeginExecuteReader to add a WaitHandle for the   
        //  process to the array.  
    {  
        connection1.Open();  
        SqlCommand command1 =  
            new SqlCommand(commandText1, connection1);  
        IAsyncResult result1 = command1.BeginExecuteNonQuery();  
        WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
        connection2.Open();  
  
        SqlCommand command2 =  
            new SqlCommand(commandText2, connection2);  
        IAsyncResult result2 = command2.BeginExecuteNonQuery();  
        WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
        connection3.Open();  
  
        SqlCommand command3 =  
            new SqlCommand(commandText3, connection3);  
        IAsyncResult result3 = command3.BeginExecuteNonQuery();  
        WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
        WaitHandle[] waitHandles = {  
            waitHandle1, waitHandle2, waitHandle3  
        };  
  
        bool result;  
        //  WaitAll waits for all of the processes to   
        //  complete. The return value is True if the processes  
        //  all completed successfully, False if any process  
        //  timed out.  
  
        result = WaitHandle.WaitAll(waitHandles, 60000, false);  
        if(result)  
        {  
            long rowCount1 =   
                command1.EndExecuteNonQuery(result1);  
            TextBox1.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
            long rowCount2 =   
                command2.EndExecuteNonQuery(result2);  
            TextBox2.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
  
            long rowCount3 =   
                command3.EndExecuteNonQuery(result3);  
            TextBox3.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
        }  
        else  
        {  
            throw new Exception("Timeout");  
        }  
    }  
  
    catch (Exception ex)  
    {  
        TextBox4.Text = ex.ToString();  
    }  
    connection1.Close();  
    connection2.Close();  
    connection3.Close();  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Asynchrone Vorgänge](asynchronous-operations.md)
