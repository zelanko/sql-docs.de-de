---
title: 'Schritt 4: Hinzufügen eines Datenflusstasks zum Paket | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c77240716811c47f28577577c89647f141fdd53f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329990"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a>Schritt 4: Hinzufügen eines Datenflusstasks zum Paket
  Nach dem Erstellen des Verbindungs-Managers für die Quell- und Zieldaten besteht die nächste Aufgabe im Hinzufügen eines Datenflusstasks zu Ihrem Paket. Der Datenflusstask kapselt die Datenfluss-Engine, von dem Daten zwischen Quellen und Zielen verschoben werden, und bietet die Funktionalität für das Transformieren, das Cleanup und das Ändern von Daten beim Verschieben. Im Datenflusstask wird der Hauptteil eines ETL-Prozesses (Extract, Transform, Load - Extrahieren, Transformieren, Laden) durchgeführt.  
  
> [!NOTE]  
>  Von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] wird der Datenfluss von der Ablaufsteuerung getrennt.  
  
### <a name="to-add-a-data-flow-task"></a>So fügen Sie einen Datenflusstask hinzu  
  
1.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Favoriten**, und ziehen Sie anschließend einen **Datenflusstask** auf die Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
    > [!NOTE]  
    >  Wenn die SSIS-Toolbox nicht verfügbar ist, wählen Sie im Hauptmenü SSIS und dann SSIS-Toolbox aus, um die SSIS-Toolbox anzuzeigen.  
  
3.  Auf der **Ablaufsteuerung** Entwurfsoberfläche zum Entwickeln der rechten Maustaste auf die neu hinzugefügte **Data Flow Task**, klicken Sie auf **umbenennen**, und ändern Sie den Namen in `Extract Sample Currency Data`.  
  
     Es empfiehlt sich, eindeutige Namen für alle Komponenten bereitzustellen, die Sie einer Entwurfsoberfläche hinzufügen. Aus Gründen der Benutzer- und Wartungsfreundlichkeit sollten die Namen die Funktion beschreiben, die jede Komponente ausführt. Das Befolgen dieser Namensrichtlinien ermöglicht die Selbstdokumentierung Ihrer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete. Eine andere Möglichkeit zur Dokumentation Ihrer Pakete besteht im Verwenden von Anmerkungen. Weitere Informationen zum Verwenden von Anmerkungen finden Sie unter [Verwenden von Anmerkungen in Paketen](use-annotations-in-packages.md).  
  
4.  Den Datenflusstask, klicken Sie auf **Eigenschaften**, und prüfen Sie im Eigenschaftenfenster, ob die `LocaleID` -Eigenschaftensatz auf **Englisch (Vereinigte Staaten)**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenflusstask](control-flow/data-flow-task.md)  
  
  
