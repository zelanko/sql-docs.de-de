---
title: 'Schritt 3: Ändern des Directory-Eigenschaftskonfigurationswertes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39a1547e2248c62299026440b5b33da88458138e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085880"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a>Schritt 3: Ändern des Directory-Eigenschaftskonfigurationswertes
  In dieser Aufgabe ändern Sie die in der Datei SSISTutorial.dtsConfig gespeicherte Konfigurationseinstellung für die Wert-Eigenschaft der Variablen `User::varFolderName` auf Paketebene. Die Variable aktualisiert die Verzeichnis-Eigenschaft des Foreach-Schleifencontainers. Der geänderte Wert zeigt auf die `New Sample Data` Ordner, den Sie in der vorherigen Aufgabe erstellt haben. Nachdem Sie die Konfigurationseinstellung geändert und das Paket ausgeführt haben, wird die Verzeichnis-Eigenschaft durch die Variable aktualisiert. Dabei wird der durch die Konfigurationsdatei aufgefüllte Wert anstelle des Verzeichniswerts verwendet, der ursprünglich im Paket konfiguriert war.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>So ändern Sie die Konfigurationseinstellung der Directory-Eigenschaft  
  
1.  Suchen und öffnen Sie in Editor oder einem beliebigen anderen Texteditor die Konfigurationsdatei SSISTutorial.dtsConfig, die Sie mithilfe des Paketkonfigurations-Assistenten in der vorhergehenden Aufgabe erstellt haben.  
  
2.  Ändern Sie den Wert von der **ConfiguredValue** Element entsprechend den Pfad des der `New Sample Data` Ordner, den Sie in der vorherigen Aufgabe erstellt haben. Schließen Sie den Pfad nicht in Anführungszeichen ein. Wenn die `New Sample Data` Ordner befindet sich im Stammverzeichnis Ihres Laufwerks (z. B. "c:"\\), der aktualisierten XML-Code sollte ähnlich wie im folgenden Beispiel werden:  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     Die Überschrifteninformationen `GeneratedBy`, `GeneratedFromPackageID`, und **GeneratedDate** unterscheiden sich in Ihrer Datei natürlich. Achten Sie insbesondere auf das `Configuration`-Element. Die `Value`-Eigenschaft der `User::varFolderName`-Variablen enthält nun den Wert C:\New Sample Data.  
  
3.  Speichern Sie die Änderung, und schließen Sie dann den Texteditor.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 4: Testen des Tutorialpakets aus Lektion 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
