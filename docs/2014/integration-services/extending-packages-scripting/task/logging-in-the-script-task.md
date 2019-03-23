---
title: Protokollieren im Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e2ab23134ef193c4dfc17c901fc7d41e1af2083d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58380918"
---
# <a name="logging-in-the-script-task"></a>Protokollieren im Skripttask
  Durch Verwendung der Protokollierung in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paketen können Sie detaillierte Informationen über Status, Ergebnisse und Probleme der Ausführung aufzeichnen, indem Sie vordefinierte Ereignisse bzw. benutzerdefinierte Meldungen für die spätere Analyse erfassen. Der Skripttask kann die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>-Methode des `Dts`-Objekts verwenden, um benutzerdefinierte Daten zu protokollieren. Wenn die Protokollierung aktiviert ist und im Dialogfeld **SSIS-Protokolle konfigurieren** auf der Registerkarte **Details** das **ScriptTaskLogEntry**-Ereignis für die Protokollierung ausgewählt ist, dann speichert ein einzelner Aufruf der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>-Methode die Ereignisinformationen in allen Protokollanbietern, die für den Task konfiguriert wurden.  
  
> [!NOTE]  
>  Obwohl Sie Protokollierungen direkt vom Skripttask aus ausführen können, ist ggf. eine Implementierung von Ereignissen einer Protokollierung vorzuziehen. Bei der Verwendung von Ereignissen können Sie nicht nur die Protokollierung von Ereignismeldungen aktivieren, sondern auch mit standardmäßigen oder benutzerdefinierten Ereignishandlern auf das Ereignis reagieren.  
  
 Weitere Informationen zur Protokollierung finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md).  
  
## <a name="logging-example"></a>Beispiel für die Protokollierung  
 Im folgenden Beispiel wird die Protokollierung vom Skripttask aus durch Protokollierung eines Werts, der die Anzahl der verarbeiteten Zeilen darstellt, gezeigt.  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Blog-Artikel, [Logging custom events for Integration Services tasks](https://go.microsoft.com/fwlink/?LinkId=165644) (Protokollieren von benutzerdefinierten Ereignissen für Integration Services-Tasks), auf „dougbert.com“  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Protokollierung &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md)  
  
  
