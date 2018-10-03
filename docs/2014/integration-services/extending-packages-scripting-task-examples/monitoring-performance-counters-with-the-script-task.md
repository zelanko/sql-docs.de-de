---
title: Überwachen von Leistungsindikatoren mit dem Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4a953f6fadd8ee9d2d89c69394b3df7ef8830929
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103010"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a>Überwachen von Leistungsindikatoren mit dem Skripttask
  Administratoren müssen möglicherweise die Leistung von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen überwachen, die komplexe Transformationen mit großen Datenmengen durchführen. Der **System.Diagnostics**-Namespace von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] umfasst Klassen zur Verwendung vorhandener sowie zur Erstellung eigener Leistungsindikatoren.  
  
 Leistungsindikatoren speichern Leistungsdaten von Anwendungen, anhand derer Sie die Leistung von Software über einen bestimmten Zeitraum analysieren können. Leistungsindikatoren können mit dem Tool **Systemmonitor** lokal oder remote überwacht werden. Für die spätere Verzweigung der Ablaufsteuerung im Paket können Sie die Werte der Leistungsindikatoren in Variablen speichern.  
  
 Als Alternative zu Leistungsindikatoren haben Sie auch die Möglichkeit, das <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>-Ereignis über die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>-Eigenschaft des `Dts`-Objekts auszulösen. Das <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>-Ereignis gibt sowohl inkrementelle Status- als auch abgeschlossene Prozentsatzinformationen an die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Laufzeit zurück.  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Im folgenden Beispiel wird ein benutzerdefinierter Leistungsindikator erstellt und anschließend inkrementiert. Zuerst wird ermittelt, ob der Leistungsindikator bereits vorhanden ist. Falls der Leistungsindikator noch nicht erstellt wurde, ruft das Skript die `Create`-Methode des `PerformanceCounterCategory`-Objekts auf, um ihn zu generieren. Anschließend inkrementiert das Skript den Leistungsindikator. Zum Abschluss wird die `Close`-Methode für den Leistungsindikator aufgerufen, sobald dieser nicht mehr benötigt wird (bewährte Methode).  
  
> [!NOTE]  
>  Zum Erstellen einer neuen Leistungsindikatorkategorie und eines Leistungsindikators sind Administratorrechte erforderlich. Außerdem bleiben die neue Kategorie und der Leistungsindikator nach der Erstellung auf dem Computer erhalten.  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
-   Verwenden einer `Imports` -Anweisung im Code zum Importieren der **System.Diagnostics** Namespace.  
  
### <a name="example-code"></a>Beispielcode  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
