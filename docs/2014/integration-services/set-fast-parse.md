---
title: Schnelle Analyse festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bb0fefd2f9c06d6bcff44c211904a951ebe01937
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963350"
---
# <a name="set-fast-parse"></a>Festlegen der schnellen Analyse
  Die Fast Parse-Eigenschaft muss für jede Spalte der Quelle oder Transformation festgelegt werden, die die schnelle Analyse verwendet. Verwenden Sie zum Festlegen der Eigenschaft den Erweiterten Editor der Flatfilequelle und der Transformation für Datenkonvertierung.  
  
### <a name="to-set-fast-parse"></a>So legen Sie die schnelle Analyse fest  
  
1.  Klicken Sie mit der rechten Maustaste auf die Flatfilequelle bzw. die Transformation für Datenkonvertierung, und klicken Sie anschließend auf **Erweiterten Editor anzeigen**.  
  
2.  Klicken Sie im Dialogfeld **Erweiterter Editor** auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** .  
  
3.  Klicken Sie im Bereich **Eingaben und Ausgaben** auf die Spalte, für die die schnelle Analyse aktiviert werden soll.  
  
4.  Erweitern Sie im Eigenschaftenfenster den Knoten **benutzerdefinierte Eigenschaften** , und legen Sie dann die- `FastParse` Eigenschaft auf fest `True` .  
  
5.  Klicken Sie auf **OK**.  
  
  
