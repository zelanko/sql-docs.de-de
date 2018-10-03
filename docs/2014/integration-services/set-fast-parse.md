---
title: Festlegen der schnellen Analyse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 960876737e552e7c5a9af75cc23d7e43e3799735
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170610"
---
# <a name="set-fast-parse"></a>Festlegen der schnellen Analyse
  Die Fast Parse-Eigenschaft muss für jede Spalte der Quelle oder Transformation festgelegt werden, die die schnelle Analyse verwendet. Verwenden Sie zum Festlegen der Eigenschaft den Erweiterten Editor der Flatfilequelle und der Transformation für Datenkonvertierung.  
  
### <a name="to-set-fast-parse"></a>So legen Sie die schnelle Analyse fest  
  
1.  Klicken Sie mit der rechten Maustaste auf die Flatfilequelle bzw. die Transformation für Datenkonvertierung, und klicken Sie anschließend auf **Erweiterten Editor anzeigen**.  
  
2.  Klicken Sie im Dialogfeld **Erweiterter Editor** auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** .  
  
3.  Klicken Sie im Bereich **Eingaben und Ausgaben** auf die Spalte, für die die schnelle Analyse aktiviert werden soll.  
  
4.  Erweitern Sie im Fenster Eigenschaften die **benutzerdefinierte Eigenschaften** Knoten, und legen anschließend die `FastParse` Eigenschaft `True`.  
  
5.  Klicken Sie auf **OK**.  
  
  
