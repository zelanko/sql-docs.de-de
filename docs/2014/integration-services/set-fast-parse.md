---
title: Festlegen der schnellen Analyse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
caps.latest.revision: 5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 79307cdd25f15f34eaaf3be084a3d46045ee7d8d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162841"
---
# <a name="set-fast-parse"></a>Festlegen der schnellen Analyse
  Die Fast Parse-Eigenschaft muss für jede Spalte der Quelle oder Transformation festgelegt werden, die die schnelle Analyse verwendet. Verwenden Sie zum Festlegen der Eigenschaft den Erweiterten Editor der Flatfilequelle und der Transformation für Datenkonvertierung.  
  
### <a name="to-set-fast-parse"></a>So legen Sie die schnelle Analyse fest  
  
1.  Klicken Sie mit der rechten Maustaste auf die Flatfilequelle bzw. die Transformation für Datenkonvertierung, und klicken Sie anschließend auf **Erweiterten Editor anzeigen**.  
  
2.  Klicken Sie im Dialogfeld **Erweiterter Editor** auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** .  
  
3.  Klicken Sie im Bereich **Eingaben und Ausgaben** auf die Spalte, für die die schnelle Analyse aktiviert werden soll.  
  
4.  Erweitern Sie im Fenster Eigenschaften die **benutzerdefinierte Eigenschaften** Knoten, und legen anschließend die `FastParse` Eigenschaft `True`.  
  
5.  Klicken Sie auf **OK**.  
  
  
