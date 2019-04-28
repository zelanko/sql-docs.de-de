---
title: Ausführen eines Pakets in SQL Server Datatools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0a4b8a1778fb7e8bcd91df82002ee068ffae22ef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889610"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>Ausführen eines Pakets in SQL Server Data Tools
  Das Ausführen von Paketen in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erfolgt zumeist beim Entwickeln, Debuggen und Testen von Paketen. Wenn Sie ein Paket im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer ausführen, wird das Paket immer sofort ausgeführt.  
  
 Während ein Paket ausgeführt wird, zeigt der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer den Fortschritt der Paketausführung auf der **Status** -Registerkarte an. Sie können den Start- und Endzeitpunkt des Pakets sowie seine Tasks und Container sehen. Außerdem werden Informationen über Tasks und Container im Paket angezeigt, deren Ausführung fehlerhaft ist. Wenn die Ausführung des Pakets beendet wurde, sind die Laufzeitinformationen weiterhin auf der Registerkarte **Ausführungsergebnisse** verfügbar. Weitere Informationen finden Sie im Abschnitt "Fortschrittsberichte" im Thema [Debugging Control Flow](control-flow/control-flow.md).  
  
 **Entwurfszeitbereitstellung**. Wenn Sie ein Paket in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]ausführen, wird das Paket erstellt und dann in einem Ordner bereitgestellt. Vor dem Ausführen des Pakets können Sie den Ordner angeben, in dem das Paket bereitgestellt wird. Wenn Sie keinen Ordner angeben, wird standardmäßig der Ordner **bin** verwendet. Dieser Bereitstellungstyp wird als Entwurfszeitbereitstellung bezeichnet.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>So führen Sie ein Paket in SQL Server-Datentools aus  
  
1.  Wenn die Projektmappe mehrere Projekte enthält, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem Paket, und klicken Sie anschließend auf **Als Startobjekt festlegen**, um das Startprojekt festzulegen.  
  
2.  Wenn das Projekt mehrere Pakete enthält, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, und klicken Sie anschließend auf **Als Startobjekt** festlegen, um das Startpaket festzulegen.  
  
3.  Sie können ein Paket mit einem der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Paket, das Sie ausführen möchten, und klicken Sie auf der Menüleiste auf **Debuggen starten** , oder drücken Sie F5. Nachdem das Paket ausgeführt wurde, drücken Sie UMSCHALT+F5, um zum Entwurfsmodus zurückzukehren.  
  
    -   Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, und klicken Sie anschließend auf **Paket ausführen**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>So geben Sie einen anderen Ordner für die Entwurfszeitbereitstellung an  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projektordner, der das auszuführende Paket enthält. Klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **\<Projektname>-Eigenschaftenseiten** auf **Erstellen**.  
  
3.  Aktualisieren Sie den Wert der OutputPath-Eigenschaft, und geben Sie den Ordner an, den Sie für die Entwurfszeitbereitstellung verwenden möchten. Klicken Sie anschließend auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)   
 [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) (Integration Services-Pakete [SSIS])  
  
  
