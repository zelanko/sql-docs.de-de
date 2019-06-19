---
title: 'Schritt 3: Ändern des Directory-Eigenschaftskonfigurationswertes | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 09d4279501110d15eab2ca339e33ddb9ab0cee3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65721214"
---
# <a name="lesson-5-3-modify-the-directory-property-configuration-value"></a>Lektion 5.3: Ändern des Directory-Eigenschaftskonfigurationswerts

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Im Rahmen dieser Aufgabe ändern Sie die in der Datei **SSISTutorial.dtsConfig** gespeicherte Konfigurationseinstellung für die **Value**-Eigenschaft der Variablen `User::varFolderName` auf Paketebene. Die Variable aktualisiert die **Directory**-Eigenschaft des Foreach-Schleifencontainers. Der geänderte Wert zeigt nun auf den Ordner **New Sample Data**, den Sie in der vorherigen Aufgabe erstellt haben. Nachdem Sie die Konfigurationseinstellung geändert und das Paket ausgeführt haben, wird die **Directory**-Eigenschaft über die Variable in der Konfigurationsdatei aktualisiert. Bisher war der Wert der **Directory**-Eigenschaft Teil des Pakets.  
  
## <a name="modify-the-configuration-setting-of-the-directory-property"></a>Ändern der Konfigurationseinstellung für die Directory-Eigenschaft  
  
1.  Suchen und öffnen Sie in Editor oder einem beliebigen anderen Text-Editor die Konfigurationsdatei **SSISTutorial.dtsConfig**, die Sie mithilfe des Paketkonfigurations-Assistenten in der vorhergehenden Aufgabe erstellt haben.  
  
2.  Ändern Sie den Wert des **ConfiguredValue** -Elements so, dass er mit dem Pfad des Ordners **New Sample Data** übereinstimmt, den Sie in der vorherigen Aufgabe erstellt haben. Schließen Sie den Pfad nicht in Anführungszeichen ein. Wenn sich der Ordner **New Sample Data** auf der Stammebene des Laufwerks (z. B. **C:\\** ) befindet, sollten die aktualisierten XML-Daten dem folgenden Beispiel ähneln:  
  
    ```
    <?xml version="1.0"?>
    <DTSConfiguration>
      <DTSConfigurationHeading>
        <DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFEE1D3FA}" GeneratedDate="6/10/2018 8:16:50 AM"/>
      </DTSConfigurationHeading>
      <Configuration ConfiguredType="Property" 
          Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String">
        <ConfiguredValue>C:\New Sample Data</ConfiguredValue>
      </Configuration>
    </DTSConfiguration>  
    ```

    Die Überschrifteninformationen **GeneratedBy**, **GeneratedFromPackageID**und **GeneratedDate** unterscheiden sich in Ihrer Datei. Achten Sie insbesondere auf das **Konfiguration** -Element. Die **Value**-Eigenschaft der Variablen `User::varFolderName` enthält nun den Wert **C:\New Sample Data**.  
  
3.  Speichern Sie die Änderung, und schließen Sie dann den Texteditor.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 4: Testen des Pakets aus Lektion 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
