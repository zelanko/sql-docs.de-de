---
title: 'Schritt 2: Überprüfen des Bereitstellungspakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f43403ee078b66226839ecc934cf83a99751f76a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273426"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>Schritt 2: Überprüfen des Bereitstellungspakets
  In Lektion 1 haben Sie das Deployment Tutorial-Projekt erstellt und dem Projekt Pakete und Hilfsdateien hinzugefügt; in der vorherigen Aufgabe haben Sie ein Bereitstellungsprogramm für das Projekt erstellt.  
  
 In dieser Aufgabe überprüfen Sie den Inhalt des Bereitstellungspakets. Das Bereitstellungspaket ist der Ordner, den Sie auf den Zielcomputer kopieren und zum Installieren der Pakete verwenden. Wenn Sie den Standardwert – bin\Deployment – als Speicherort des Bereitstellungshilfsprogramms verwendet haben, entspricht das Bereitstellungspaket dem Ordner Bin\Deployment im Ordner Deployment Tutorial des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts.  
  
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
  
4.  Überprüfen Sie, ob den Wert des der `AllowConfigurationChanges` -Attribut ist **"true"** und der XML-Code enthält eine `Package` -Element für die beiden Pakete, eine `MiscellaneousFile` -Element für jede der vier nichtpaketdateien, und ein `ConfigurationFile` -Element für jeden der zwei XML-Konfigurationsdateien.  
  
5.  Beenden Sie Internet Explorer oder den Texteditor.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Installieren von Paketen](../integration-services/lesson-3-install-ssis-package.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
