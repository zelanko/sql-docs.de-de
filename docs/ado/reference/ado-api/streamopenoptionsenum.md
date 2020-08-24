---
description: StreamOpenOptionsEnum
title: StreamOpenOptionsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
author: rothja
ms.author: jroth
ms.openlocfilehash: 80918159031787844330c4ddd92032e81a99c8c1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777189"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Gibt Optionen für das Öffnen eines Daten [Strom](./stream-object-ado.md) Objekts an. Die Werte können mit einem or-Vorgang kombiniert werden.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**Adoption-streamasync**|1|Öffnet das **Stream** -Objekt im asynchronen Modus.|  
|**"adopendstreamfromrecord"**|4|Identifiziert den Inhalt des *Quell* Parameters als bereits geöffnetes [Daten Satz](./record-object-ado.md) Objekt. Das Standardverhalten besteht darin, die *Quelle* als URL zu behandeln, die direkt auf einen Knoten in einer Baumstruktur verweist. Der Standarddaten Strom, der diesem Knoten zugeordnet ist, wird geöffnet.|  
|**"adopendstreamunspezifiziert"**|-1|Standard. Gibt an, dass das **Stream** -Objekt mit Standardoptionen geöffnet wird.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO-Datenstrom)](./open-method-ado-stream.md)