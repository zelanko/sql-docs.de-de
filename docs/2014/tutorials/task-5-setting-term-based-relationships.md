---
title: 'Aufgabe 5: Festlegen von Begriffs basierten Beziehungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0e9a6a1a96d208077e70c0cf1835cff6e34650dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489111"
---
# <a name="task-5-setting-term-based-relationships"></a>Aufgabe 5: Festlegung begriffsbasierter Beziehungen
  In dieser Aufgabe definieren Sie einige Begriffs basierte Beziehungen für Werte für die Domäne **Supplier Name** . Eine Begriffs basierte Beziehung ermöglicht es Ihnen, eine Korrektur an einem Begriff vorzunehmen, der Teil eines Werts in einer Domäne ist. Mehrere Werte, die abgesehen von der Schreibweise eines gemeinsamen Teils identisch sind, werden als identische Synonyme angesehen. Beispielsweise kann **Inc.** in **integriert**werden. DQS verwendet diese Beziehungen bei der Wissensermittlung, Bereinigung oder beim Abgleich. Weitere Informationen finden Sie unter [Erstellen von Begriffs basierten Beziehungen](https://msdn.microsoft.com/library/hh510404.aspx) .  
  
1.  Wählen Sie in der **Liste Domäne**den **Namen Lieferanten Name** aus.  
  
2.  Wechseln Sie im rechten Bereich zur Registerkarte **Begriffs basierte Beziehungen** .  
  
3.  Klicken Sie auf der Symbolleiste auf neue Beziehungs Schaltfläche **Hinzufügen** , um der Tabelle eine Beziehung hinzuzufügen.  
  
4.  Geben Sie **Co.** für das Feld **Wert** und **Unternehmen** für das Feld **korrigieren in** ein.  
  
5.  Wiederholen Sie die beiden vorherigen Schritten für folgende Werte:  
  
    |value|Korrigieren in|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Begriffsbasierte Beziehungen](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Begriffsbasierte Beziehungen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Festlegen von Synonymen](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
