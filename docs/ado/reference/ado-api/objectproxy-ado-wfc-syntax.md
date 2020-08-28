---
description: ObjectProxy (ADO/WFC-Syntax)
title: ObjectProxy (ADO-WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 1c52f9253ced985ed6a53af87c95ff7fe2eee3fa
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990401"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO/WFC-Syntax)
Ein **ObjectProxy** -Objekt stellt einen Server dar und wird von der Methode " **kreateobject** " des [DataSpace](../rds-api/dataspace-object-rds.md) -Objekts zurückgegeben. Die ObjectProxy-Klasse verfügt über eine Methode, die **aufgerufen**wird, die eine Methode auf dem Server aufrufen und ein Objekt zurückgeben kann, das sich aus diesem Aufruf ergibt.  
  
 **Paket "com. ms. wfc. Data"**  
  
## <a name="methods"></a>Methoden  
  
### <a name="call-method-adowfc-syntax"></a>Callmethode (ADO/WFC-Syntax)  
 Ruft eine Methode auf dem Server auf, der durch den ObjectProxy dargestellt wird. Optional können Methodenargumente als Array von-Objekten übermittelt werden.  
  
#### <a name="syntax"></a>Syntax  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Gibt zurück  
 Object  
 Ein Objekt, das sich aus dem Aufrufen der Methode ergibt.  
  
#### <a name="parameters"></a>Parameter  
 *ObjectProxy*  
 Ein **ObjectProxy** -Objekt, das den Server darstellt.  
  
 *method*  
 Eine Zeichenfolge, die den Namen der Methode enthält, die auf dem Server aufgerufen werden soll.  
  
 *args*  
 Optional. Ein Array von-Objekten, die Argumente für die-Methode auf dem Server sind. Java-Datentypen werden automatisch in Datentypen konvertiert, die für die Verwendung auf dem Server geeignet sind.