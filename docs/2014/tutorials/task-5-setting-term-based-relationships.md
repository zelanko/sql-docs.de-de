---
title: 'Aufgabe 5: Festlegung Begriffsbasierter Beziehungen basierend | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8450d3e77de578810bb57c35aafad6f90c8f19c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046017"
---
# <a name="task-5-setting-term-based-relationships"></a>Aufgabe 5: Festlegung begriffsbasierter Beziehungen
  In dieser Aufgabe definieren Sie ein paar begriffsbasierte Beziehungen für Werte für die **Lieferantenname** Domäne. Eine begriffsbasierte Beziehung können Sie eine Korrektur an einem Begriff vornehmen, die Teil eines Werts in einer Domäne ist. Mehrere Werte, die abgesehen von der Schreibweise eines gemeinsamen Teils identisch sind, werden als identische Synonyme angesehen. Beispielsweise **Inc.** behoben werden können, um **Incorporated**. DQS verwendet diese Beziehungen bei der Wissensermittlung, Bereinigung oder beim Abgleich. Finden Sie unter [erstellen begriffsbasierte Beziehungen](http://msdn.microsoft.com/library/hh510404.aspx) Weitere Details.  
  
1.  Wählen Sie **Lieferantenname** in der **Domänenliste**.  
  
2.  Wechseln Sie zu der **begriffsbasierte Beziehungen** Registerkarte im rechten Bereich.  
  
3.  Klicken Sie auf **neue Beziehung hinzufügen** Schaltfläche auf der Symbolleiste, um eine Beziehung zur Tabelle hinzufügen.  
  
4.  Typ **Co.** für die **Wert** Feld und **Unternehmen** für die **korrigieren in** Feld.  
  
5.  Wiederholen Sie die beiden vorherigen Schritten für folgende Werte:  
  
    |value|Korrigieren in|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Begriffsbasierte Beziehungen](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "begriffsbasierte Beziehungen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Festlegen von Synonymen](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  