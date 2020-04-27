---
title: Verwenden von Variablen in der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 922454c7bc04a211d6f54754d48331fdfdffeb07
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62894969"
---
# <a name="using-variables-in-the-script-component"></a>Verwenden von Variablen in der Skriptkomponente
  Variablen speichern Werte, die von einem Paket und dessen Containern, Tasks und Ereignishandlern zur Laufzeit verwendet werden können. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services-ssis-variables.md).  
  
 Sie können vorhandene Variablen für schreibgeschützten oder Lese-/Schreibzugriff für Ihr benutzerdefiniertes Skript verfügbar machen, indem Sie durch Trennzeichen getrennte Listen `ReadOnlyVariables` von `ReadWriteVariables` Variablen in den Feldern und auf der Seite **Skript** des **Transformations-Editors für Skript**Erstellung eingeben. Beachten Sie, dass bei Variablennamen nach Groß-/Kleinschreibung unterschieden wird. Mithilfe der `Value`-Eigenschaft erhalten Sie Lese- und Schreibzugriff auf einzelne Variablen. Die Skriptkomponente führt erforderliche Sperrungen im Hintergrund aus, da das Skript die Variablen zur Laufzeit verarbeitet.  
  
> [!IMPORTANT]  
>  Die Auflistung von `ReadWriteVariables` ist nur in der `PostExecute`-Methode verfügbar, um das Risiko von Sperrkonflikten zu vermindern und die Leistung zu maximieren. Sie können daher den Wert einer Paketvariablen nicht direkt inkrementieren, während Sie jede Datenzeile verarbeiten. Inkrementieren Sie stattdessen den Wert einer lokalen Variablen, und legen Sie den Wert der Paketvariablen auf den Wert der lokalen Variablen in der `PostExecute`-Methode fest, nachdem alle Daten verarbeitet wurden. Sie können auch die Eigenschaft <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> verwenden, um diese Einschränkung zu umgehen, wie später in diesem Thema beschrieben ist. Wenn Sie jedoch direkt in eine Paketvariable schreiben, während jede Zeile verarbeitet wird, wird die Leistung beeinträchtigt und das Risiko von Sperrkonflikten erhöht.  
  
 Weitere Informationen über die Seite **Skript** im **Transformations-Editor für Skripterstellung** finden Sie unter [Konfigurieren der Skriptkomponente im Skriptkomponenten-Editor](configuring-the-script-component-in-the-script-component-editor.md) und [Transformations-Editor für Skripterstellung &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).  
  
 Die Skriptkomponente erstellt eine `Variables`-Auflistungsklasse im `ComponentWrapper`-Projektelement mit einer Accessoreigenschaft mit starker Typbindung für den Wert jeder vorkonfigurierten Variable, wobei die Eigenschaft denselben Namen wie die Variable selbst hat. Diese Auflistung wird von der `Variables`-Eigenschaft der `ScriptMain`-Klasse verfügbar gemacht. Die Accessoreigenschaft bietet entsprechend Lese- oder Lese-/Schreibberechtigung für den Wert der Variable. Wenn Sie beispielsweise eine Ganzzahlvariable namens `MyIntegerVariable` zur Liste `ReadOnlyVariables` hinzugefügt haben, können Sie ihren Wert mit dem folgenden Code in das Skript abrufen:  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 Für die Arbeit mit Variablen in der Skriptkomponente können Sie auch die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>-Eigenschaft (Aufruf mit `Me.VariableDispenser`) verwenden. In diesem Fall verwenden Sie nicht die benannten, typisierten Accessoreigenschaften für Variablen, sondern greifen direkt auf die Variablen zu. Bei der Verwendung von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> müssen Sie die Sperrsemantik und die Umwandlung von Datentypen für variable Werte in Ihrem Code berücksichtigen. Wenn Sie mit Variablen arbeiten möchten, die zur Entwurfszeit nicht zur Verfügung stehen, sondern programmgesteuert zur Laufzeit erstellt werden, müssen Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>-Eigenschaft statt der benannten, typisierten Accessoreigenschaften verwenden.  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Variablen](../../integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../use-variables-in-packages.md)  
  
  
