---
description: RecordTypeEnum
title: Recordtypeumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e5a43d2b53a76a21d79ce671004e139dab5e20
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771989"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Gibt den Typ des [Daten Satz](./record-object-ado.md) Objekts an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adsimplerecord**|0|Gibt einen *einfachen* Datensatz an (enthält keine untergeordneten Knoten).|  
|**adcollectionrecord**|1|Gibt einen *Sammlungs* Daten Satz an (enthält untergeordnete Knoten).|  
|**adrecordunknown**|-1|Gibt an, dass der Typ dieses **Datensatzes** unbekannt ist.|  
|**adstructdoc**|2|Gibt eine besondere Art von *Sammlungs* Daten Satz an, der com-strukturierte Dokumente darstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [RecordType-Eigenschaft (ADO)](./recordtype-property-ado.md)