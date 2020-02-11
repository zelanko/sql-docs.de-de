---
title: Konfigurieren von Prüfpunkten zum erneuten Starten eines fehlerhaften Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e22e47af568ecf723b54a35fb6b83bd5ce74e333
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060771"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>Konfigurieren von Prüfpunkten zum erneuten Starten eines fehlerhaften Pakets
  Sie können ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket so konfigurieren, dass nicht das gesamte Paket erneut ausgeführt wird, sondern ab dem Punkt, an dem ein Fehler auftrat. Hierzu legen Sie die Eigenschaften fest, die für Prüfpunkte gelten.  
  
### <a name="to-configure-a-package-to-restart"></a>So konfigurieren Sie den Neustart eines Pakets  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie konfigurieren möchten.  
  
2.  Doppelklicken Sie in **Projektmappen-Explorer**auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im Hintergrund der Entwurfsoberfläche der Ablaufsteuerung, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Legen Sie die SaveCheckpoints- `True`Eigenschaft auf fest.  
  
6.  Geben Sie den Namen der Prüfpunktdatei in die CheckpointFileName-Eigenschaft ein.  
  
7.  Legen Sie die CheckpointUsage-Eigenschaft auf einen der beiden Werte fest:  
  
    -   Wählen Sie `Always` aus, damit das Paket immer am Prüfpunkt neu gestartet wird.  
  
        > [!IMPORTANT]  
        >  Falls die Prüfpunktdatei nicht verfügbar ist, tritt ein Fehler auf.  
  
    -   Wählen Sie `IfExists` aus, damit das Paket nur neu gestartet wird, wenn die Prüfpunktdatei verfügbar ist.  
  
8.  Konfigurieren Sie die Tasks und Container, von denen das Paket neu gestartet werden kann.  
  
    -   Klicken Sie mit der rechten Maustaste auf einen Task oder Container, und klicken Sie anschließend auf **Eigenschaften**.  
  
    -   Legen Sie die FailPackageOnFailure- `True` Eigenschaft für jeden ausgewählten Task und Container auf fest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neustarten von Paketen mit Prüfpunkten](packages/restart-packages-by-using-checkpoints.md)  
  
  
