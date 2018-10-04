---
title: Zurückgeben von Ergebnissen aus dem Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7883016021d40578401d1d7d0c5d894959693bdf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074580"
---
# <a name="returning-results-from-the-script-task"></a>Zurückgeben von Ergebnissen aus dem Skripttask
  Der Skripttask verwendet die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>- und die optionale <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>-Eigenschaft, um Statusinformationen an die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Laufzeit zurückzugeben, die zur Bestimmung des Pfads des Workflows nach Abschluss des Skripttasks verwendet werden können.  
  
## <a name="taskresult"></a>TaskResult  
 Die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>-Eigenschaft berichtet, ob der Task erfolgreich war oder zu einem Fehler geführt hat. Zum Beispiel:  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 Die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>-Eigenschaft gibt optional ein benutzerdefiniertes Objekt zurück, das das erfolgreiche Ausführen oder Fehlschlagen des Skripttasks misst oder weitere Informationen darüber liefert. Der FTP-Task verwendet beispielsweise die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>-Eigenschaft, um die Anzahl von übertragenen Dateien zurückzugeben. Der Task „SQL ausführen“ gibt die Anzahl von Zeilen zurück, auf die sich der Task ausgewirkt hat. Der <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> kann auch verwendet werden, um den Pfad des Workflows zu bestimmen. Zum Beispiel:  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
