---
title: Erkennen einer leeren flachen Datei mit dem Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 34462589141133e04ca8728361e3a173f0944f12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895499"
---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a>Erkennen einer leeren flachen Datei mit dem Skripttask
  Die Flatfilequelle ermittelt vor dem Verarbeitungsversuch nicht, ob eine Flatfile Datenzeilen enthält. Möglicherweise möchten Sie die Effizienz eines Pakets verbessern, insbesondere bei Paketen, die eine Iteration durch zahlreiche Faltfiles durchführen. Dazu können Sie die Dateien auslassen, die keine Datenzeilen enthalten. Der Skripttask kann nach leeren Flatfiles suchen, bevor das Paket mit der Verarbeitung des Datenflusses beginnt.  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Im folgenden Beispiel wird mithilfe von Methoden des `System.IO`-Namespace das in einem Verbindungs-Manager für Flatfiles angegebene Flatfile getestet, um zu ermitteln, ob die Datei leer ist oder ob sie nur erwartete Nichtdatenzeilen wie z. B. Spaltenkopfzeilen oder eine leere Zeile enthält. Das Skript prüft zuerst die Größe der Datei; bei einer Größe von 0 (null) Bytes ist die Datei leer. Ist die Datei größer als 0 (null), liest das Skript die Zeilen aus der Datei so lange, bis keine weiteren Zeilen mehr vorhanden sind, oder bis die Anzahl der Zeilen höher ist als die erwartete Anzahl der Nichtdatenzeilen. Ist die Anzahl der Zeilen der Datei kleiner oder gleich der erwarteten Anzahl der Nichtdatenzeilen, dann wird davon ausgegangen, dass die Datei leer ist. Das Ergebnis wird dann als boolescher Wert in einer Benutzervariablen zurückgegeben, deren Wert für die Verzweigung in der Paketablaufsteuerung verwendet werden kann. Die `FireInformation` Methode zeigt auch das Ergebnis in der **Ausgabe** Fenster die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
1.  Erstellen und konfigurieren Sie einen Flatfile-Verbindungs-Manager, die mit dem Namen `EmptyFlatFileTest`.  
  
2.  Erstellen Sie eine ganzzahlige Variable mit dem Namen `FFNonDataRows` und legen sie ihren Wert auf die Anzahl der in der Flatfile erwarteten Nichtdatenzeilen fest.  
  
3.  Erstellen Sie eine boolesche Variable mit dem Namen `FFIsEmpty`.  
  
4.  Fügen Sie die `FFNonDataRows`-Variable der Eigenschaft **ReadOnlyVariables** des Skripttasks hinzu.  
  
5.  Fügen Sie die `FFIsEmpty`-Variable der Eigenschaft **ReadWriteVariables** des Skripttasks hinzu.  
  
6.  Importieren Sie in Ihrem Code den `System.IO`-Namespace.  
  
 Bei der Iteration durch Dateien mit einem Foreach-Schleifen-Editor müssen Sie anstelle der Verwendung eines einzelnen Flatfile-Verbindungs-Managers den unten aufgeführten Beispielcode ändern, um den Namen und Pfad der Datei von der Variable, in der der Enumerationswert gespeichert ist, und nicht vom Verbindungsmanager, zu erhalten.  
  
### <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Skripttask-Beispiele](../extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
