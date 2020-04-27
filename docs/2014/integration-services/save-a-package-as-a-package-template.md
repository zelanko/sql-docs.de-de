---
title: Speichern eines Pakets als Paket Vorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 76349c0ca91f24a6d8d7942a89eb9683a91b573d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056339"
---
# <a name="save-a-package-as-a-package-template"></a>Speichern eines Pakets als Paketvorlage
  In diesem Thema wird beschrieben, wie Sie beim Erstellen neuer Integration Services-Pakete in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]benutzerdefinierte Pakete als Vorlagen festlegen und verwenden. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] verwendet standardmäßig eine Paketvorlage, die ein leeres Paket erstellt, wenn Sie einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt ein neues Paket hinzufügen. Sie können diese Standardvorlage nicht ersetzen. Es können jedoch neue Vorlagen hinzugefügt werden.  
  
 Sie haben die Möglichkeit, mehrere Pakete als Vorlagen festzulegen. Sie müssen zunächst benutzerdefinierte Pakete erstellen, bevor Sie diese als Vorlagen implementieren können.  
  
 Wenn Sie benutzerdefinierte Pakete als Vorlagen zum Erstellen von Paketen verwenden, haben die neuen Pakete denselben Namen und GUID wie die Vorlage. Sie sollten den Wert der `Name`-Eigenschaft aktualisieren und einen neuen GUID für die `ID`-Eigenschaft generieren, um die Pakete voneinander zu unterscheiden. Weitere Informationen finden Sie unter [Erstellen von Paketen in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) und [Festlegen von Paketeigenschaften](set-package-properties.md).  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a>So legen Sie ein benutzerdefiniertes Paket als Paketvorlage fest  
  
1.  Suchen Sie im Dateisystem nach dem Paket, welches Sie als Vorlage verwenden möchten.  
  
2.  Kopieren Sie das Paket in den Ordner DataTransformationItems. Dieser Ordner befindet sich standardmäßig unter C:\Programme\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
3.  Wiederholen Sie die Schritte 1 und 2 für jedes als Vorlage zu verwendende Paket.  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a>So verwenden Sie ein benutzerdefiniertes Paket als Paketvorlage  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, in dem Sie ein Paket erstellen möchten.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
3.  Klicken Sie im Dialogfeld **neues\<Element hinzufügen-Projektname>** auf das Paket, das Sie als Vorlage verwenden möchten.  
  
     Die Vorlagenliste enthält die Standardpaketvorlage mit der Bezeichnung Neues SSIS-Paket. Das Paketsymbol identifiziert die als Paketvorlage verwendbaren Vorlagen.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Paketen in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) (Integration Services-Pakete [SSIS])  
  
  
