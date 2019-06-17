---
title: Abfragen des Active Directory mit dem Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bbcea29ad75eb84b9c8099e5998e307ecbd7943c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62895029"
---
# <a name="querying-the-active-directory-with-the-script-task"></a>Abfragen des Active Directory mit dem Skripttask
  Anwendungen für die Verarbeitung von Unternehmensdaten, wie z. B. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete, müssen Daten häufig je nach Stellung, Berufsbezeichnung und anderen im Active Directory gespeicherten Eigenschaften der Mitarbeiter unterschiedlich verarbeiten. Active Directory ist ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Verzeichnisdienst, der einen zentralen Speicher für Metadaten nicht nur über Benutzer, sondern auch über andere Werte des Unternehmens, wie etwa über Computer und Drucker, bereitstellt. Der `System.DirectoryServices`-Namespace in Microsoft .NET Framework stellt Klassen für die Verwendung mit Active Directory bereit, sodass Sie den Datenverarbeitungsworkflow anhand der darin gespeicherten Informationen weiterleiten können.  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Im folgenden Beispiel werden Name, Titel und Telefonnummer eines Mitarbeiters anhand des Werts der `email`-Variable, die die E-Mail-Adresse des Mitarbeiters enthält, aus dem Active Directory abgerufen. Mithilfe von Rangfolgeneinschränkungen im Paket kann anhand der abgerufenen Informationen und der Berufsbezeichnung des Mitarbeiters beispielsweise bestimmt werden, ob eine E-Mail-Nachricht mit niedriger Priorität oder eine Seite mit hoher Priorität gesendet werden soll.  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
1.  Erstellen Sie die drei Zeichenfolgenvariablen `email`, `name` und `title`. Geben Sie eine gültige Unternehmens-E-Mail-Adresse als Wert der `email`-Variable ein.  
  
2.  Auf der **Skript** auf der Seite die **Skripttask-Editor**, Hinzufügen der `email` -Variable auf die `ReadOnlyVariables` Eigenschaft.  
  
3.  Fügen Sie die Variablen `name` und `title` zur `ReadWriteVariables`-Eigenschaft hinzu.  
  
4.  Fügen Sie im Skriptprojekt dem `System.DirectoryServices`-Namespace einen Verweis hinzu.  
  
5.  . Verwenden Sie im Code eine `Imports`-Anweisung, um den `DirectoryServices`-Namespace zu importieren.  
  
> [!NOTE]  
>  Damit dieses Skript ausgeführt werden kann, muss im Netzwerk des Unternehmens Active Directory verwendet werden. Zudem müssen die in diesem Beispiel verwendeten Mitarbeiterinformationen im Unternehmen gespeichert werden.  
  
### <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Technischer Artikel – [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588) (Verarbeiten von Active Directory-Informationen in SSIS) – unter „social.technet.microsoft.com“  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
