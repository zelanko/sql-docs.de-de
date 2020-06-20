---
title: Ausführen eines Pakets in SQL Server Data Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ae5924e5fc1cad91b5e1511c61556ece70138dcb
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964547"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>Ausführen eines Pakets in SQL Server Data Tools
  Das Ausführen von Paketen in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erfolgt zumeist beim Entwickeln, Debuggen und Testen von Paketen. Wenn Sie ein Paket im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer ausführen, wird das Paket immer sofort ausgeführt.  
  
 Während ein Paket ausgeführt wird, [!INCLUDE[ssIS](../includes/ssis-md.md)] zeigt der-Designer den Fortschritt der Paket **Progress** Ausführung auf der Registerkarte Status an. Sie können die Start-und Abschlusszeit des Pakets und dessen Tasks und Container sowie Informationen zu allen Tasks oder Containern im Paket anzeigen, bei denen ein Fehler aufgetreten ist. Nachdem die Ausführung des Pakets abgeschlossen ist, sind die Laufzeitinformationen auf der Registerkarte **Ausführungs Ergebnisse** weiterhin verfügbar. Weitere Informationen finden Sie im Abschnitt "Progress Reporting" im Thema [Debuggen der Ablauf Steuerung](control-flow/control-flow.md).  
  
 **Entwurfszeitbereitstellung**. Wenn Sie ein Paket in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]ausführen, wird das Paket erstellt und dann in einem Ordner bereitgestellt. Vor dem Ausführen des Pakets können Sie den Ordner angeben, in dem das Paket bereitgestellt wird. Wenn Sie keinen Ordner angeben, wird standardmäßig der Ordner **bin** verwendet. Dieser Bereitstellungstyp wird als Entwurfszeitbereitstellung bezeichnet.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>So führen Sie ein Paket in SQL Server-Datentools aus  
  
1.  Wenn die Projektmappe mehrere Projekte enthält, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, und klicken Sie anschließend auf **Als Startobjekt festlegen** , um das Startprojekt festzulegen.  
  
2.  Wenn das Projekt mehrere Pakete enthält, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, und klicken Sie anschließend auf **Als Startobjekt** festlegen, um das Startpaket festzulegen.  
  
3.  Sie können ein Paket mit einem der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Paket, das Sie ausführen möchten, und klicken Sie auf der Menüleiste auf **Debuggen starten** , oder drücken Sie F5. Nachdem das Paket ausgeführt wurde, drücken Sie UMSCHALT+F5, um zum Entwurfsmodus zurückzukehren.  
  
    -   Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, und klicken Sie anschließend auf **Paket ausführen**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>So geben Sie einen anderen Ordner für die Entwurfszeitbereitstellung an  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projektordner, der das auszuführende Paket enthält. Klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld ** \<project name> Eigenschaften Seiten** auf **Erstellen**.  
  
3.  Aktualisieren Sie den Wert der OutputPath-Eigenschaft, und geben Sie den Ordner an, den Sie für die Entwurfszeitbereitstellung verwenden möchten. Klicken Sie anschließend auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)   
 [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) (Integration Services-Pakete [SSIS])  
  
  
