---
title: ConnectOptionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9df3fd695e9bf281133dabf436e5e8b5de7e0b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309160"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Gibt an, ob die [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt sollte nach dem Herstellen der Verbindung (synchron) oder vor dem zurückgeben (asynchron).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Öffnet die Verbindung asynchron aus. Die [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) Ereignis kann verwendet werden, um zu bestimmen, wenn die Verbindung verfügbar ist.|  
|**adConnectUnspecified**|-1|Standard. Öffnet die Verbindung synchron aus.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)
