---
title: ObjectProxy (ADO / WFC-Syntax) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af28755fee20c478237edec22936fc694995d554
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63459404"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO/WFC-Syntax)
Ein **ObjectProxy** Objekt steht für einen Server, und wird zurückgegeben, indem die **CreateObject** Methode der [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt. Die ObjectProxy-Klasse verfügt über eine Methode, **Aufrufen**, das Aufrufen einer Methode auf dem Server und ein Objekt, das durch diesen Aufruf zurückgeben können.  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>Methoden  
  
### <a name="call-method-adowfc-syntax"></a>Rufen Sie die Methode (ADO/WFC-Syntax)  
 Ruft eine Methode auf dem Server, die durch die ObjectProxy dargestellt wird. Optional können die Methodenargumente als ein Array von Objekten übergeben werden.  
  
#### <a name="syntax"></a>Syntax  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Rückgabewert  
 Objekt  
 Ein Objekt, das durch Aufrufen der Methode.  
  
#### <a name="parameters"></a>Parameter  
 *ObjectProxy*  
 Ein **ObjectProxy** -Objekt, das den Server darstellt.  
  
 *method*  
 Eine Zeichenfolge, mit dem Namen der Methode, die auf dem Server aufgerufen werden soll.  
  
 *args*  
 Dies ist optional. Ein Array von Objekten, die Argumente der Methode auf dem Server sind. Java-Datentypen werden in Datentypen, die für die Verwendung auf dem Server geeignet automatisch konvertiert.
