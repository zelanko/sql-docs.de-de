---
title: Verwenden von Rückrufen in Windows-Anwendungen
description: Bietet ein Beispiel, das zeigt, wie ein asynchroner Befehl sicher ausgeführt werden kann, wobei die Interaktion mit einem Formular und dessen Inhalt in einem separaten Thread ordnungsgemäß gehandhabt wird.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e8c5fbecb8892639e5e4e0cb608c3c4de0447508
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896014"
---
# <a name="windows-applications-using-callbacks"></a>Verwenden von Rückrufen in Windows-Anwendungen

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

In den meisten asynchronen Verarbeitungsszenarien möchten Sie einen Datenbankvorgang starten und andere Prozesse fortsetzen, ohne auf den Abschluss des Datenbankvorgangs warten zu müssen. In vielen Szenarien muss jedoch nach Abschluss des Datenbankvorgangs noch etwas erfolgen. In einer Windows-Anwendung beispielsweise ermöglicht das Delegieren des Vorgangs mit langer Ausführungszeit an einen Hintergrundthread, dass der Benutzeroberflächenthread reaktionsfähig bleibt. Wenn der Datenbankvorgang jedoch abgeschlossen ist, möchten Sie die Ergebnisse zum Ausfüllen des Formulars verwenden. Diese Art von Szenario lässt sich am besten mit einem Rückruf umsetzen.  
  
Sie definieren einen Rückruf, indem Sie in der Methode <xref:System.AsyncCallback>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> oder <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> einen <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>-Delegaten angeben. Der Delegat wird aufgerufen, wenn der Vorgang abgeschlossen ist. Sie können an den Delegaten einen Verweis auf den <xref:Microsoft.Data.SqlClient.SqlCommand> selbst übergeben, wodurch der Zugriff auf das <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt und der Aufruf der entsprechenden `End`-Methode problemlos möglich ist, ohne dass eine globale Variable verwendet werden muss.  
  
## <a name="example"></a>Beispiel  
Die folgende Windows-Anwendung veranschaulicht die Verwendung der <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>-Methode, bei der (zum Emulieren eines Befehls mit langer Ausführungszeit) eine Transact-SQL-Anweisung mit einer Verzögerung von einigen Sekunden ausgeführt wird.  
  
Dieses Beispiel veranschaulicht eine Reihe wichtiger Techniken, einschließlich des Aufrufs einer Methode, die in einem separaten Thread mit dem Formular interagiert. Darüber hinaus zeigt dieses Beispiel, wie Sie die gleichzeitige Ausführung eines Befehls durch Benutzer mehrmals blockieren und wie sicherstellen müssen, dass das Formular nicht geschlossen wird, bevor die Rückrufprozedur aufgerufen wird.  
  
Um dieses Beispiel einzurichten, erstellen Sie eine neue Windows-Anwendung. Platzieren Sie ein <xref:System.Windows.Forms.Button>-Steuerelement und zwei <xref:System.Windows.Forms.Label>-Steuerelemente auf dem Formular (wobei der Standardname für jedes Steuerelement übernommen wird). Fügen Sie der Klasse des Formulars den folgenden Code hinzu, wobei Sie die Verbindungszeichenfolge entsprechend Ihrer Umgebung ändern müssen.  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on   
// the form's design surface in Visual Studio), and then add   
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus   
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the   
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object   
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,              
    // you can retrieve it from a configuration file.   
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for   
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the   
            // SqlCommand object as the second parameter in the   
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that   
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.   
        DisplayInfoDelegate del =   
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,   
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't   
        // handle it here. You can either log the exception or   
        // invoke a delegate (as in the non-error case in this   
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a   
        // delegate as in the try block here.   
  
        // You can create the delegate instance as you   
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Asynchrone Vorgänge](asynchronous-operations.md)
