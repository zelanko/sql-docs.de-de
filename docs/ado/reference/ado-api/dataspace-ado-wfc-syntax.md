---
description: DataSpace (ADO/WFC-Syntax)
title: DataSpace (ADO-WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: rothja
ms.author: jroth
ms.openlocfilehash: 6fdc89f6fb9c1c32236d7e4da02ad2afb118ba08
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974251"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO/WFC-Syntax)
Die Methode " **kreateobject** " der **DataSpace** -Klasse gibt sowohl ein Geschäftsobjekt an, um Client Anwendungsanforderungen (*ProgID*) als auch das Kommunikationsprotokoll und den Server (*Verbindung*) zu verarbeiten. " **kreateobject** " gibt ein [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) -Objekt zurück, das den Server darstellt.  
  
## <a name="package-commswfcdata"></a>Paket "com. ms. wfc. Data"  
  
### <a name="constructor"></a>Konstruktor  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Methoden  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
