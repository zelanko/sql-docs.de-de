---
title: Editor für den Datenprofilerstellungs-Task (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 00d151f80439062ca67a1320d4453155079a332e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047856"
---
# <a name="data-profiling-task-editor-general-page"></a>Editor für den Datenprofilerstellungs-Task (Seite "Allgemein")
  Verwenden Sie die Seite **Allgemein** im **Editor für den Datenprofilerstellungs-Task** , um die folgenden Optionen zu konfigurieren:  
  
-   Geben Sie das Ziel für die Profilausgabe an.  
  
-   Verwenden Sie die Standardeinstellungen, um den Task der Profilerstellung für eine einzelne Tabelle oder Sicht zu vereinfachen.  
  
 Weitere Informationen zum Verwenden des Datenprofilerstellungs-Tasks finden Sie unter [Einrichten von Datenprofilerstellungs-Tasks](data-profiling-task.md). Weitere Informationen zum Verwenden des Datenprofil-Viewers zum Analysieren der Ausgabe des Datenprofilerstellungs-Tasks finden Sie unter [Datenprofil-Viewer](data-profile-viewer.md).  
  
 **So öffnen Sie die Seite 'Allgemein' des Editors für den Datenprofilerstellungs-Task**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, das den Datenprofilerstellungs-Task enthält.  
  
2.  Doppelklicken Sie auf der Registerkarte **Ablaufsteuerung** auf den Datenprofilerstellungs-Task.  
  
3.  Klicken Sie im **Editor für den Datenprofilerstellungs-Task**auf **Allgemein**.  
  
## <a name="data-profiling-options"></a>Datenprofilerstellungs-Optionen  
 **Timeout**  
 Geben Sie die Anzahl der Sekunden an, nach der ein Timeout des Datenprofilerstellungs-Tasks erfolgt und die Taskausführung abgebrochen wird. Der Standardwert ist 0, d. h., es erfolgt kein Timeout.  
  
## <a name="destination-options"></a>Zieloptionen  
  
> [!IMPORTANT]  
>  Die Ausgabedatei enthält möglicherweise vertrauliche Daten über Ihre Datenbank und die darin enthaltenen Daten. Vorschläge zur Verbesserung der Sicherheit dieser Datei finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../access-to-files-used-by-packages.md).  
  
 **DestinationType**  
 Geben Sie an, ob die Datenprofilausgabe in einer Datei oder einer Variablen gespeichert werden soll:  
  
|value|Description|  
|-----------|-----------------|  
|**FileConnection**|Speichert die Profilausgabe in einer Datei an dem in einem Dateiverbindungs-Manager angegebenen Speicherort.<br /><br /> Hinweis: Sie geben mit der Option **Ziel** an, welcher Dateiverbindungs-Manager verwendet werden soll.|  
|**Variable**|Speichert die Profilausgabe in einer Paketvariablen.<br /><br /> Hinweis: Sie geben mit der Option **Ziel** an, welche Paketvariable verwendet werden soll.|  
  
 **Ziel**  
 Geben Sie an, welcher Dateiverbindungs-Manager oder welche Paketvariable die Datenprofilausgabe enthält:  
  
-   Wenn die **DestinationType** -Option auf **FileConnection**festgelegt wird, zeigt die Option **Ziel** die verfügbaren Dateiverbindungs-Manager an. Wählen Sie einen dieser Verbindungs-Manager aus, oder wählen Sie \<Neue Dateiverbindung> aus, um einen neuen Dateiverbindungs-Manager zu erstellen.  
  
-   Wenn die **DestinationType** -Option auf **Variable**festgelegt wird, zeigt die Option **Ziel** die verfügbaren Paketvariablen in der Liste **Ziel** an. Wählen Sie eine dieser Variablen aus, oder wählen Sie \<Neue Variable> aus, um eine neue Variable zu erstellen.  
  
 **OverwriteDestination**  
 Geben Sie an, ob die Ausgabedatei überschrieben werden soll, wenn sie bereits vorhanden ist. Der Standardwert ist **False**. Der Wert dieser Eigenschaft wird nur verwendet, wenn die DestinationType-Option auf FileConnection festgelegt wird. Wenn die DestinationType-Option auf Variable festgelegt wird, überschreibt der Task immer den vorherigen Wert der Variablen.  
  
> [!IMPORTANT]  
>  Wenn Sie versuchen, den Datenprofilerstellungs-Task mehrmals auszuführen, ohne den Namen der Ausgabedatei zu ändern oder den Wert der **OverwriteDestination** -Eigenschaft in **True**zu ändern, schlägt der Task mit der Meldung fehl, dass die Ausgabedatei bereits vorhanden ist.  
  
## <a name="other-options"></a>Weitere Optionen  
 **Schnellprofil**  
 Öffnet das **Schnellprofilformular für eine einzelne Tabelle**. Dieses Formular vereinfacht den Task der Profilerstellung für eine einzelne Tabelle oder Sicht anhand von Standardeinstellungen. Weitere Informationen finden Sie unter [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md).  
  
 **Profil-Viewer öffnen**  
 Öffnet den Datenprofil-Viewer. Der eigenständige Datenprofil-Viewer zeigt die Datenprofilausgabe des Datenprofilerstellungs-Tasks an. Sie können die Datenprofilausgabe anzeigen, nachdem Sie den Datenprofilerstellungs-Task innerhalb des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets ausgeführt und die Datenprofile berechnet haben.  
  
> [!NOTE]  
>  Sie können auch den Datenprofil-Viewer öffnen, indem Sie die Datei „DataProfileViewer.exe“ im Ordner *\<Laufwerk>*:\Programme (x86) | Programme\Microsoft SQL Server\110\DTS\Binn ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Single Table Schnellprofil Form &#40;Datenprofilerstellungs-Task&#41;](single-table-quick-profile-form-data-profiling-task.md)   
 [Editor für den Datenprofilerstellungs-Task &#40;Seite „Profilanforderungen“&#41;](data-profiling-task-editor-profile-requests-page.md)  
  
  