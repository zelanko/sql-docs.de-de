---
title: Erfassen einer Liste für die ForEach-Schleife mit dem Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a876962d68d081542c7c5032c1bf06a0e527fe4c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155050"
---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a>Erfassen einer Liste für die ForEach-Schleife mit dem Skripttask
  Der Foreach-Enumerator für Daten aus Variable führt die Elemente in einer Liste auf, die ihm in einer Variablen übergeben wird, und führt für alle Elemente dieselben Aufgaben aus. Sie können benutzerdefinierten Code in einem Skripttask verwenden, um eine Liste für diesen Zweck zu erstellen. Weitere Informationen zum Enumerator finden Sie unter [Foreach Loop Container](../control-flow/foreach-loop-container.md) (Foreach-Schleifencontainer).  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Im folgenden Beispiel werden Methoden des `System.IO`-Namespace verwendet, um eine Liste von Excel-Arbeitsmappen auf dem Computer zu sammeln, die älter oder neuer als eine vom Benutzer in der Variablen definierte Anzahl von Tagen sind. Verzeichnisse des Laufwerks C werden rekursiv nach Dateien durchsucht, die eine .xls-Erweiterung aufweisen. Anschließend wird das Datum der letzten Änderung der Datei überprüft, um festzustellen, ob die Datei in die Liste gehört. Geeignete Dateien werden einer `ArrayList` hinzugefügt, und die `ArrayList` wird für die spätere Verwendung in einem Foreach-Schleifencontainer in einer Variablen gespeichert. Der Foreach-Schleifencontainer wird für die Verwendung des Foreach-Enumerators für Daten aus Variable konfiguriert.  
  
> [!NOTE]  
>  Variablen, die Sie mit dem Foreach-Enumerator für Daten aus Variable verwenden, müssen den Typ `Object` aufweisen. Objekte, die Sie in den Variablen platzieren, müssen eine der folgenden Schnittstellen implementieren: `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource` oder `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`. Häufig wird ein `Array` oder eine `ArrayList` verwendet. Die `ArrayList` erfordert einen Verweis und eine `Imports`-Anweisung für den `System.Collections`-Namespace.  
  
 Sie können mit diesem Task experimentieren, indem Sie verschiedene positive und negative Werte für die Paketvariable `FileAge` einsetzen. Sie können z. B. den Wert 5 eingeben, um nach Dateien zu suchen, die in den letzten fünf Tagen erstellt wurden, oder den Wert -3 für Dateien, die vor mehr als drei Tagen angelegt wurden. Diese Aufgabe kann bei Laufwerken, die viele zu durchsuchende Ordner enthalten, ein bis zwei Minuten in Anspruch nehmen.  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
1.  Erstellen Sie eine Paketvariable vom Typ integer mit dem Namen `FileAge`, und geben Sie einen positiven oder negativen ganzzahligen Wert ein. Ist der Wert positiv, sucht der Code nach Dateien, die neuer als die angegebene Anzahl von Tagen ist. Bei negativen Werten wird nach Dateien gesucht, die älter als die genannte Anzahl von Tagen sind.  
  
2.  Erstellen Sie eine Paketvariable vom Typ `Object` mit dem Namen `FileList`, um zur späteren Verwendung mit dem Foreach-Enumerator für Daten aus Variable die Liste der Dateien aufzunehmen, die vom Skripttask erfasst wurden.  
  
3.  Fügen Sie die `FileAge`-Variable der `ReadOnlyVariables`-Eigenschaft des Skripttasks sowie die `FileList`-Variable der `ReadWriteVariables`-Eigenschaft hinzu.  
  
4.  Importieren Sie in Ihren Code die Namespaces `System.Collections` und `System.IO`.  
  
### <a name="code"></a>Code  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Foreach Loop Container](../control-flow/foreach-loop-container.md)  (Foreach-Schleifencontainer)  
 [Konfigurieren eines Foreach-Schleifencontainers](../configure-a-foreach-loop-container.md)  
  
  
