---
description: ConnectOptionEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 71142aac94003987267a6d4a6b30d2c9d17c1bfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444422"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Gibt an, ob die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode eines [Connection](../../../ado/reference/ado-api/connection-object-ado.md) -Objekts zurückgegeben werden soll, nachdem die Verbindung (synchron) oder vor (asynchron) hergestellt wurde.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adasyncconnect**|16|Öffnet die Verbindung asynchron. Das Ereignis [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) kann verwendet werden, um zu bestimmen, wann die Verbindung verfügbar ist.|  
|**adconnectunspezifiziert**|-1|Standard. Öffnet die Verbindung synchron.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoumums. connectoption. asyncconnect|  
|Adoesums. connectoption. connectunspezifiziert|  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)
