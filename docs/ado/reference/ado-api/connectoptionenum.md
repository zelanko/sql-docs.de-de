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
ms.openlocfilehash: 819fb89d7f8c43e76ba9260a72fafa68084bf880
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933446"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Gibt an, ob die [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt sollte nach dem Herstellen der Verbindung (synchron) oder vor dem zurückgeben (asynchron).  
  
|Konstante|Wert|Beschreibung|  
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
