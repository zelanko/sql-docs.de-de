---
title: Verwenden von Variablen im Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 55122ec1323c0e95816af4e6129f324041ab2eda
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967160"
---
# <a name="using-variables-in-the-script-task"></a>Verwenden von Variablen im Skripttask
  Variablen ermöglichen es dem Skripttask, Daten mit anderen Objekten im Paket auszutauschen. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services-ssis-variables.md).  
  
 Mithilfe der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>-Eigenschaft des `Dts`-Objekts erhält der Skripttask Lese- und Schreibzugriff auf <xref:Microsoft.SqlServer.Dts.Runtime.Variable>-Objekte im Paket.  
  
> [!NOTE]  
>  Die <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Dts.Runtime.Variable>-Klasse ist vom Typ `Object`. Da für den Skripttask `Option Strict` aktiviert ist, müssen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>-Eigenschaft vor ihrer Verwendung in den richtigen Typ umwandeln.  
  
 Um bestehende Variablen für das benutzerdefinierte Skript verfügbar zu machen, fügen Sie diese den Listen <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> und <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> im **Skripttask-Editor** hinzu. Beachten Sie, dass bei Variablennamen nach Groß-/Kleinschreibung unterschieden wird. Innerhalb des Skripts greifen Sie auf Variablen beider Typen über die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>-Eigenschaft des `Dts`-Objekts zu. Mithilfe der `Value`-Eigenschaft erhalten Sie Lese- und Schreibzugriff auf einzelne Variablen. Der Skripttask verwaltet Sperren transparent, während das Skript die Werte von Variablen liest und ändert.  
  
 Mithilfe der <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Runtime.Variables>-Auflistung, die von der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>-Eigenschaft zurückgegeben wird, können Sie das Vorhandensein von Variablen vor ihrer Verwendung im Code überprüfen.  
  
 Für die Arbeit mit Variablen im Skripttask können Sie auch die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>-Eigenschaft (Dts.VariableDispenser) verwenden. Bei der Verwendung von <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> müssen Sie die Sperrsemantik und die Umwandlung von Datentypen für variable Werte in Ihrem Code berücksichtigen. Wenn Sie mit Variablen arbeiten möchten, die zur Entwurfszeit nicht zur Verfügung stehen, sondern programmgesteuert zur Laufzeit erstellt werden, müssen Sie möglicherweise auf die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>-Eigenschaft anstelle der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>-Eigenschaft zurückgreifen.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Verwenden des Skripttasks in einem Foreach-Schleifencontainer  
 Wenn ein Skripttask wiederholt innerhalb eines Foreach-Schleifencontainers ausgeführt wird, muss das Skript normalerweise auf den Inhalt des aktuellen Elements im Enumerator zugreifen. Bei der Verwendung eines Foreach-Dateienumerators muss das Skript beispielsweise über den aktuellen Dateinamen verfügen und bei der Verwendung eines Foreach-ADO-Enumerators über den Inhalt der Spalten in der aktuellen Datenzeile.  
  
 Variablen ermöglichen diese Kommunikation zwischen dem Foreach-Schleifencontainer und dem Skripttask. Weisen Sie jedem Datenelement, das von einem Enumerationselement zurückgegeben wird, im **Foreach-Schleifen-Editor** auf der Seite **Variablenzuordnungen** Variablen zu. Ein Foreach-Dateienumerator gibt z. B. nur am Index 0 einen Dateinamen zurück und erfordert daher nur eine Variablenzuordnung. Bei einem Enumerator, der in jeder Zeile mehrere Datenspalten zurückgibt, müssen Sie hingegen für jede Spalte, die Sie im Skripttask verwenden möchten, eine andere Variable zuordnen.  
  
 Nachdem Sie den Variablen Enumerationselemente zugeordnet haben, müssen Sie die zugeordneten Variablen der `ReadOnlyVariables` Eigenschaft auf der Seite **Skript** im **Skript Task-Editor** hinzufügen, um Sie für das Skript verfügbar zu machen. Ein Beispiel eines Skripttasks innerhalb eines Foreach-Schleifencontainers zur Verarbeitung der Bilddateien in einem Ordner finden Sie unter [Arbeiten mit Bildern mithilfe des Skripttasks](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Variablenbeispiel  
 Das folgende Beispiel veranschaulicht den Zugriff auf und die Verwendung von Variablen in einem Skripttask zur Ermittlung des Pfads eines Paket-Workflows. Im Beispiel wird davon ausgegangen, dass Sie ganzzahlige Variablen mit dem Namen `CustomerCount` und erstellt `MaxRecordCount` und Sie der-Auflistung `ReadOnlyVariables` im **Skript Task-Editor**hinzugefügt haben. Die `CustomerCount`-Variable enthält die Anzahl an Kundendatensätzen, die importiert werden sollen. Falls der Wert höher als der Wert von `MaxRecordCount` ist, gibt der Skripttask eine Fehlermeldung aus. Falls der Fehler auftritt, weil der `MaxRecordCount`-Schwellenwert überschritten wurde, kann der Fehlerpfad des Workflows alle erforderlichen Cleanup-Schritte implementieren.  
  
 Um das Beispiel erfolgreich zu kompilieren, müssen Sie einen Verweis auf die Microsoft.SqlServer.ScriptTask-Assembly hinzufügen.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
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
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Variablen](../../integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../use-variables-in-packages.md)  
  
  
