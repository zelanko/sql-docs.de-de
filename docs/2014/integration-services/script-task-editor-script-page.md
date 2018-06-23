---
title: Skripttask-Editor (Skriptseite) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0b5641a837761e113368eea47777c3c3bf82ee20
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163154"
---
# <a name="script-task-editor-script-page"></a>Skripttask-Editor (Seite Skript)
  Mithilfe der Seite **Skript** des Dialogfelds **Skripttask-Editor** können Sie Skripteigenschaften festlegen und Variablen angeben, auf die dieses Skript zugreifen kann.  
  
> [!NOTE]  
>  In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] und höheren Versionen werden alle Skripts vorkompiliert. In früheren Versionen wurde eine **PrecompileScriptIntoBinaryCode** -Eigenschaft festgelegt, um anzugeben, dass das Skript vorkompiliert wurde.  
  
 Weitere Informationen zum Skripttask finden Sie unter [Script Task](control-flow/script-task.md) und [Konfigurieren des Skripttasks im Skripttask-Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Informationen zum Programmieren des Skripttasks finden Sie unter [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Tastatur  
 **ScriptLanguage**  
 Wählen Sie die Skriptsprache für den Task aus, entweder [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic oder [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Nachdem Sie ein Skript für den Task erstellt haben, können Sie den Wert der **ScriptLanguage** -Eigenschaft nicht mehr ändern.  
  
 Um die Standardskriptsprache für den Skripttask festzulegen, verwenden Sie im Dialogfeld **Optionen** auf der Seite **Allgemein** die Option **Skriptsprache** . Weitere Informationen finden Sie unter [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Geben Sie die Methode an, die die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Laufzeit als Einstiegspunkt in den Code des Skripttasks aufruft. Die angegebene Methode muss in der ScriptMain-Klasse des Projekts der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Tools für Anwendungen (VSTA) angegeben werden. ScriptMain ist die Standardklasse, die von den Skriptvorlagen generiert wird.  
  
 Wenn Sie den Namen der Methode im VSTA-Projekt geändert haben, müssen Sie den Wert der **EntryPoint** -Eigenschaft ändern.  
  
 **ReadOnlyVariables**  
 Geben Sie eine durch Trennzeichen getrennte Liste von schreibgeschützten Variablen ein, die für das Skript verfügbar sind, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**…**), und wählen Sie die Variablen im Dialogfeld **Variablen auswählen** aus.  
  
> [!NOTE]  
>  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
 **ReadWriteVariables**  
 Geben Sie eine durch Trennzeichen getrennte Liste von Lese-/Schreibvariablen ein, die für das Skript verfügbar sind, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**…**), und wählen Sie die Variablen im Dialogfeld **Variablen auswählen** aus.  
  
> [!NOTE]  
>  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
 **Skript bearbeiten**  
 Öffnet die VSTA IDE, in der Sie das Skript erstellen oder ändern können.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seite "Allgemein"](general-page-of-integration-services-designers-options.md)   
 [Skripttask-Editor &#40;Seite "Allgemein"&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [Skripttask-Beispiele](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integrationsservices &#40;SSIS&#41; Variablen](integration-services-ssis-variables.md)   
 [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  