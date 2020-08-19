---
description: ObjectProxy (ADO/WFC-Syntax)
title: ObjectProxy (ADO-WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
author: rothja
ms.author: jroth
ms.openlocfilehash: 7809c1b9ce4d090ed63465061045ea04000f47dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443032"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO/WFC-Syntax)
Ein **ObjectProxy** -Objekt stellt einen Server dar und wird von der Methode " **kreateobject** " des [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) -Objekts zurückgegeben. Die ObjectProxy-Klasse verfügt über eine Methode, die **aufgerufen**wird, die eine Methode auf dem Server aufrufen und ein Objekt zurückgeben kann, das sich aus diesem Aufruf ergibt.  
  
 **Paket "com. ms. wfc. Data"**  
  
## <a name="methods"></a>Methoden  
  
### <a name="call-method-adowfc-syntax"></a>Callmethode (ADO/WFC-Syntax)  
 Ruft eine Methode auf dem Server auf, der durch den ObjectProxy dargestellt wird. Optional können Methodenargumente als Array von-Objekten übermittelt werden.  
  
#### <a name="syntax"></a>Syntax  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Rückgabe  
 Object  
 Ein Objekt, das sich aus dem Aufrufen der Methode ergibt.  
  
#### <a name="parameters"></a>Parameter  
 *ObjectProxy*  
 Ein **ObjectProxy** -Objekt, das den Server darstellt.  
  
 *method*  
 Eine Zeichenfolge, die den Namen der Methode enthält, die auf dem Server aufgerufen werden soll.  
  
 *args*  
 Optional. Ein Array von-Objekten, die Argumente für die-Methode auf dem Server sind. Java-Datentypen werden automatisch in Datentypen konvertiert, die für die Verwendung auf dem Server geeignet sind.
