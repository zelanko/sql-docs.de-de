---
title: 'Schritt 4: Hinzufügen eines Datenflusstasks zum Paket | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 37275d31837a700f5e69c433630839529c2ac0ae
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965280"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a>Schritt 4: Hinzufügen eines Datenflusstasks zum Paket
  Nach dem Erstellen des Verbindungs-Managers für die Quell- und Zieldaten besteht die nächste Aufgabe im Hinzufügen eines Datenflusstasks zu Ihrem Paket. Der Datenflusstask kapselt die Datenfluss-Engine, von der Daten zwischen Quellen und Zielen verschoben werden, und bietet die Funktionalität für das Transformieren, das Cleanup und das Ändern von Daten beim Verschieben. Im Datenflusstask wird der Hauptteil eines ETL-Prozesses (Extract, Transform, Load - Extrahieren, Transformieren, Laden) durchgeführt.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]trennt den Datenfluss von der Ablauf Steuerung.  
  
### <a name="to-add-a-data-flow-task"></a>So fügen Sie einen Datenflusstask hinzu  
  
1.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Favoriten**, und ziehen Sie anschließend einen **Datenflusstask** auf die Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
    > [!NOTE]  
    >  Wenn die SSIS-Toolbox nicht verfügbar ist, wählen Sie im Hauptmenü SSIS und dann SSIS-Toolbox aus, um die SSIS-Toolbox anzuzeigen.  
  
3.  Klicken Sie auf der Entwurfs Oberfläche **Ablauf Steuerung** mit der rechten Maustaste auf den neu hinzugefügten **Datenfluss Task**, klicken Sie auf **Umbenennen**, und ändern Sie den Namen in `Extract Sample Currency Data` .  
  
     Es empfiehlt sich, eindeutige Namen für alle Komponenten bereitzustellen, die Sie einer Entwurfsoberfläche hinzufügen. Aus Gründen der Benutzer- und Wartungsfreundlichkeit sollten die Namen die Funktion beschreiben, die jede Komponente ausführt. Das Befolgen dieser Namensrichtlinien ermöglicht die Selbstdokumentierung Ihrer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete. Eine andere Möglichkeit zur Dokumentation Ihrer Pakete besteht im Verwenden von Anmerkungen. Weitere Informationen zum Verwenden von Anmerkungen finden Sie unter [Verwenden von Anmerkungen in Paketen](use-annotations-in-packages.md).  
  
4.  Klicken Sie mit der rechten Maustaste auf den Datenfluss Task, klicken Sie auf **Eigenschaften**, und überprüfen Sie im Eigenschaftenfenster, ob die- `LocaleID` Eigenschaft auf **Englisch (USA)** festgelegt ist.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenflusstask](control-flow/data-flow-task.md)  
  
  
