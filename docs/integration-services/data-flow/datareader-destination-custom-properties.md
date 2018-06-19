---
title: Benutzerdefinierte Eigenschaften des DataReader-Ziels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 40eac0ed658d7a09c0f570fd157432c137101340
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35330974"
---
# <a name="datareader-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des DataReader-Ziels
  Das DataReader-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des DataReader-Ziels. Alle Eigenschaften außer **DataReader** weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|und Beschreibung|  
|-------------------|---------------|-----------------|  
|DataReader|Zeichenfolge|Der Klassenname des DataReader-Ziels.|  
|FailOnTimeout|Boolean|Gibt an, ob ein Fehler ausgegeben wird, wenn ein **ReadTimeout** auftritt. Der Standardwert dieser Eigenschaft ist **False**.|  
|ReadTimeout|Integer|Die Anzahl von Millisekunden, bevor ein Timeout auftritt. Der Standardwert dieser Eigenschaft beträgt 30000 (30 Sekunden).|  
  
 Die Eingabe und die Eingabespalten des DataReader-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [DataReader Destination](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
