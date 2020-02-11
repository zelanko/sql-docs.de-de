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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933446"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Gibt an, ob die [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode eines [Connection](../../../ado/reference/ado-api/connection-object-ado.md) -Objekts zurückgegeben werden soll, nachdem die Verbindung (synchron) oder vor (asynchron) hergestellt wurde.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adasyncconnect**|16|Öffnet die Verbindung asynchron. Das Ereignis [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) kann verwendet werden, um zu bestimmen, wann die Verbindung verfügbar ist.|  
|**adconnectunspezifiziert**|-1|Default. Öffnet die Verbindung synchron.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoumums. connectoption. asyncconnect|  
|Adoesums. connectoption. connectunspezifiziert|  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)
