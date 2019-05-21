---
title: Benutzerdefinierte Eigenschaften des DataReader-Ziels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 38c0854947ee9b853d8638593aea1e60d40941ca
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65726942"
---
# <a name="datareader-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des DataReader-Ziels

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Das DataReader-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des DataReader-Ziels. Alle Eigenschaften außer **DataReader** weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|DataReader|Zeichenfolge|Der Klassenname des DataReader-Ziels.|  
|FailOnTimeout|Boolean|Gibt an, ob ein Fehler ausgegeben wird, wenn ein **ReadTimeout** auftritt. Der Standardwert dieser Eigenschaft ist **False**.|  
|ReadTimeout|Integer|Die Anzahl von Millisekunden, bevor ein Timeout auftritt. Der Standardwert dieser Eigenschaft beträgt 30000 (30 Sekunden).|  
  
 Die Eingabe und die Eingabespalten des DataReader-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [DataReader Destination](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
