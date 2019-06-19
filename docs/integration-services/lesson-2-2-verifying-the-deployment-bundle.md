---
title: 'Schritt 2: Überprüfen des Bereitstellungspakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4d9db7052463dfbc15df62357d9fffba7def05ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65722509"
---
# <a name="lesson-2-2---verifying-the-deployment-bundle"></a>Lektion 2-2: Überprüfen des Bereitstellungspakets

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


In Lektion 1 haben Sie das Deployment Tutorial-Projekt erstellt und dem Projekt Pakete und Hilfsdateien hinzugefügt; in der vorherigen Aufgabe haben Sie ein Bereitstellungsprogramm für das Projekt erstellt.  
  
In dieser Aufgabe überprüfen Sie den Inhalt des Bereitstellungspakets. Das Bereitstellungspaket ist der Ordner, den Sie auf den Zielcomputer kopieren und zum Installieren der Pakete verwenden. Wenn Sie den Standardwert, bin\Deployment, als Speicherort des Bereitstellungshilfsprogramms verwendet haben, entspricht das Bereitstellungspaket dem Ordner „Bin\Deployment“ im Ordner „Deployment Tutorial“ des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekts.  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>So überprüfen Sie den Inhalt des Bereitstellungspakets  
  
1.  Suchen Sie den Ordner bin\Deployment auf dem Computer.  
  
2.  Überprüfen Sie, ob die folgenden Dateien vorhanden sind:  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  Klicken Sie mit der rechten Maustaste auf Deployment Tutorial.SSISDeploymentManifest, zeigen Sie auf **Öffnen mit**, und klicken Sie anschließend auf **Internet Explorer**. Sie können die Datei auch in einem Texteditor, wie z. B. dem Editor, öffnen. Der XML-Code für die Datei sollte folgendermaßen lauten:  
  
    `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  Überprüfen Sie, ob der Wert des Attributs **AllowConfigurationChanges** **TRUE** lautet und ob der XML-Code je ein **Paket** -Element für die beiden Pakete, je ein **MiscellaneousFile** -Element für die vier Nichtpaketdateien und je ein **ConfigurationFile** -Element für die beiden XML-Konfigurationsdateien enthält.  
  
5.  Beenden Sie Internet Explorer oder den Texteditor.  
  
## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 3: Installieren von SSIS-Paketen](../integration-services/lesson-3-install-ssis-packages.md)  
  
  
  
