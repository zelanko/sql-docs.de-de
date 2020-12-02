---
description: 'Lektion 1-4: Hinzufügen eines Datenflusstasks zum Paket'
title: 'Schritt 4: Hinzufügen eines Datenflusstasks zum Paket | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4d920b5f78d2d3e6dd3e557cbac4e50ad7952884
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88449671"
---
# <a name="lesson-1-4-add-a-data-flow-task-to-the-package"></a>Lektion 1-4: Hinzufügen eines Datenflusstasks zum Paket

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Nachdem Sie die Verbindungs-Manager für die Quell- und die Zieldaten erstellt haben, fügen Sie einen Datenflusstasks zu Ihrem Paket hinzu. Im Datenflusstask ist die Datenfluss-Engine definiert, über die Daten zwischen Quellen und Zielen verschoben werden, und der Task bietet die Funktionalität für das Transformieren, das Cleanup und das Ändern von Daten beim Verschieben. Im Datenflusstask wird der Hauptteil eines ETL-Prozesses (Extract, Transform, Load - Extrahieren, Transformieren, Laden) durchgeführt.  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Trennt den Datenfluss von der Ablaufsteuerung.  
  
## <a name="add-a-data-flow-task"></a>Hinzufügen eines Datenflusstasks  
  
1.  Wählen Sie die Registerkarte **Ablaufsteuerung** aus.  
  
2.  Erweitern Sie im Bereich **SSIS-Toolbox** die Option **Favoriten**, und ziehen Sie anschließend einen **Datenflusstask** auf die Entwurfsoberfläche der Registerkarte **Ablaufsteuerung**.  
  
    > [!NOTE]  
    > Wenn die SSIS-Toolbox nicht verfügbar ist, wählen Sie das Menü **SSIS** aus, und wählen Sie dann **SSIS-Toolbox** aus, um die Toolbox anzuzeigen.  

3.  Klicken Sie auf der **Ablaufsteuerung**-Entwurfsoberfläche mit der rechten Maustaste auf den neuen **Datenflusstask**, wählen Sie **Umbenennen** aus, und ändern Sie den Namen in **Extract Sample Currency Data**.  
  
    Geben Sie eindeutige Namen für alle Komponenten an, die Sie einer Entwurfsoberfläche hinzufügen. Aus Gründen der Benutzer- und Wartungsfreundlichkeit sollten die Namen die Funktion jeder Komponente beschreiben. Das Befolgen dieser Namensrichtlinien ermöglicht die Selbstdokumentierung Ihrer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete. Eine andere Möglichkeit zur Dokumentation Ihrer Pakete besteht im Verwenden von Anmerkungen. Weitere Informationen zum Verwenden von Anmerkungen finden Sie unter [Verwenden von Anmerkungen in Paketen](../integration-services/use-annotations-in-packages.md).  
  
4.  Klicken Sie mit der rechten Maustaste auf den Datenflusstask, wählen Sie **Eigenschaften** aus, und prüfen Sie im Eigenschaftenfenster, ob die **LocaleID**-Eigenschaft auf **Englisch (USA)** festgelegt ist.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Datenflusstask](../integration-services/control-flow/data-flow-task.md)  
  
  
  
