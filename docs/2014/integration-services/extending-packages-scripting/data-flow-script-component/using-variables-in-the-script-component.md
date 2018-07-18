---
title: Verwenden von Variablen in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8556b2ceb0da2c533bead385380956351413aba2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291056"
---
# <a name="using-variables-in-the-script-component"></a>Verwenden von Variablen in der Skriptkomponente
  Variablen speichern Werte, die von einem Paket und dessen Containern, Tasks und Ereignishandlern zur Laufzeit verwendet werden können. Weitere Informationen finden Sie unter [Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md).  
  
 Sie können vorhandene Variablen verfügbar machen für schreibgeschützten oder Lese-/Schreibzugriff mittels eines benutzerdefinierten Skripts durch Eingabe von durch Trennzeichen getrennte Listen von Variablen in der `ReadOnlyVariables` und `ReadWriteVariables` Felder der **Skript** auf der Seite die **Transformations-Editor**. Beachten Sie, dass bei Variablennamen nach Groß-/Kleinschreibung unterschieden wird. Mithilfe der `Value`-Eigenschaft erhalten Sie Lese- und Schreibzugriff auf einzelne Variablen. Die Skriptkomponente führt erforderliche Sperrungen im Hintergrund aus, da das Skript die Variablen zur Laufzeit verarbeitet.  
  
> [!IMPORTANT]  
>  Die Auflistung von `ReadWriteVariables` ist nur in der `PostExecute`-Methode verfügbar, um das Risiko von Sperrkonflikten zu vermindern und die Leistung zu maximieren. Sie können daher den Wert einer Paketvariablen nicht direkt inkrementieren, während Sie jede Datenzeile verarbeiten. Inkrementieren Sie stattdessen den Wert einer lokalen Variablen, und legen Sie den Wert der Paketvariablen auf den Wert der lokalen Variablen in der `PostExecute`-Methode fest, nachdem alle Daten verarbeitet wurden. Sie können auch die Eigenschaft <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> verwenden, um diese Einschränkung zu umgehen, wie später in diesem Thema beschrieben ist. Wenn Sie jedoch direkt in eine Paketvariable schreiben, während jede Zeile verarbeitet wird, wird die Leistung beeinträchtigt und das Risiko von Sperrkonflikten erhöht.  
  
 Weitere Informationen zu den **Skript** auf der Seite die **Transformations-Editor**, finden Sie unter [Configuring the Script Component in the Script Component Editor] (() Configuring-the-Script-Component-in-the-Script-Component-Editor.MD) und [Transformations-Editor &#40;Seite "Skript"&#41;](../../script-transformation-editor-script-page.md).  
  
 Die Skriptkomponente erstellt eine `Variables`-Auflistungsklasse im `ComponentWrapper`-Projektelement mit einer Accessoreigenschaft mit starker Typbindung für den Wert jeder vorkonfigurierten Variable, wobei die Eigenschaft denselben Namen wie die Variable selbst hat. Diese Auflistung wird von der `Variables`-Eigenschaft der `ScriptMain`-Klasse verfügbar gemacht. Die Accessoreigenschaft bietet entsprechend Lese- oder Lese-/Schreibberechtigung für den Wert der Variable. Wenn Sie beispielsweise eine Ganzzahlvariable namens `MyIntegerVariable` zur Liste `ReadOnlyVariables` hinzugefügt haben, können Sie ihren Wert mit dem folgenden Code in das Skript abrufen:  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 Für die Arbeit mit Variablen in der Skriptkomponente können Sie auch die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>-Eigenschaft (Aufruf mit `Me.VariableDispenser`) verwenden. In diesem Fall verwenden Sie nicht die benannten, typisierten Accessoreigenschaften für Variablen, sondern greifen direkt auf die Variablen zu. Bei der Verwendung von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> müssen Sie die Sperrsemantik und die Umwandlung von Datentypen für variable Werte in Ihrem Code berücksichtigen. Wenn Sie mit Variablen arbeiten möchten, die zur Entwurfszeit nicht zur Verfügung stehen, sondern programmgesteuert zur Laufzeit erstellt werden, müssen Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>-Eigenschaft statt der benannten, typisierten Accessoreigenschaften verwenden.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services  **<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integrationsdienste &#40;SSIS&#41; Variablen](../../integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../use-variables-in-packages.md)  
  
  
