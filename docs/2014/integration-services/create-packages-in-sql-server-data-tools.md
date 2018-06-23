---
title: Erstellen von Paketen in SQL Server Data Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f28ab22eea6e07cd855e9ff6c8e1ddcbedbbce54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150638"
---
# <a name="create-packages-in-sql-server-data-tools"></a>Erstellen von Paketen in SQL Server-Datentools
  Die Pakete, die Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer erstellen, werden im Dateisystem gespeichert. Zum Speichern eines Pakets in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder im Paketspeicher müssen Sie eine Kopie des Pakets speichern. Weitere Informationen finden Sie unter [Erstellen einer Kopie eines Miningmodells](../../2014/integration-services/save-a-copy-of-a-package.md).  
  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]können Sie mit einer der folgenden Methoden ein neues Paket erstellen:  
  
-   Verwenden der Paketvorlage in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
-   Verwenden Sie eine benutzerdefinierte Vorlage.  
  
     Sie müssen nur die als Vorlage zu verwendenden benutzerdefinierten Pakete zum Erstellen neuer Pakete in den DataTransformationItems-Ordner kopieren. Dieser Ordner befindet sich standardmäßig unter C:\Programme\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
-   Kopieren Sei ein vorhandenes Paket.  
  
     Wenn vorhandene Pakete Funktionen enthalten, die Sie wiederverwenden möchten, können Sie die Ablaufsteuerung und die Datenflüsse des neuen Pakets schneller erstellen, indem Sie aus den anderen Paketen Objekte kopieren und diese im neuen Paket einfügen. Weitere Informationen zu Kopier- und Einfügevorgängen in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] finden Sie unter [Wiederverwenden von Paketobjekten](reuse-of-package-objects.md).  
  
     Beim Erstellen eines neuen Pakets durch Kopieren eines vorhandenen Pakets oder mithilfe eines benutzerdefinierten Pakets, welches als Vorlage dient, werden Name und GUID des vorhandenen Pakets ebenfalls kopiert. Sie sollten den Namen und GUID des neuen Pakets aktualisieren, um das neue Paket vom Paket, von dem es kopiert wurde, zu unterscheiden. Beispielsweise können bei Paketen mit demselben GUID die Pakete, zu denen die Protokolldaten gehören, schwieriger identifiziert werden. Sie können erneut generieren, die GUID in der `ID` Eigenschaft und aktualisieren Sie den Wert von der `Name` Eigenschaft mithilfe des Eigenschaftenfensters in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [Festlegen von Paketeigenschaften](set-package-properties.md) und [dtutil (Hilfsprogramm)](dtutil-utility.md).  
  
-   Verwenden Sie ein benutzerdefiniertes Paket, das Sie als Vorlage festgelegt haben.  
  
-   Ausführen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import/Export-Assistenten  
  
     Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import/Export-Assistent erstellt ein vollständiges Paket für einen einfachen Import oder Export. Dieser Assistent konfiguriert die Verbindungen, die Quelle und das Ziel und fügt alle Datentransformationen hinzu, die Sie zum sofortigen Ausführen des Imports oder Exports benötigen. Optional können Sie das Paket speichern, um es zu einem späteren Zeitpunkt auszuführen oder in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]zu verfeinern und zu erweitern. Wenn Sie das Paket speichern, müssen Sie es jedoch zunächst einem vorhandenen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzufügen, bevor Sie das Paket ändern oder in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]ausführen können.  
  
 Die folgenden Verfahren wird beschrieben, wie erstellen oder Löschen eines Pakets in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Unter [Erstellen eines Basispakets (SQL Server-Video)](http://go.microsoft.com/fwlink/?LinkId=131023)können Sie ein Video abspielen, in dem das Erstellen eines Basispakets mithilfe der Standardpaketvorlage veranschaulicht wird.  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>So erstellen Sie ein Paket in SQL Server-Datentools mithilfe der Paketvorlage  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, in dem Sie ein Paket erstellen möchten.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner **SSIS-Pakete** , und klicken Sie dann auf **Neues SSIS-Paket**.  
  
3.  Fügen Sie dem Paket optional Ablaufsteuerungen, Datenflusstasks und Ereignishandler hinzu. Weitere Informationen finden Sie unter [Ablaufsteuerung](control-flow/control-flow.md), [Datenfluss](data-flow/data-flow.md) und [Integration Services-Ereignishandler &#40;SSIS&#41;](integration-services-ssis-event-handlers.md).  
  
4.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das neue Paket zu speichern.  
  
    > [!NOTE]  
    >  Es ist möglich, ein leeres Paket zu speichern.  
  
  