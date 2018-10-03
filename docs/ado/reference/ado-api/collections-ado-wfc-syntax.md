---
title: Collections (ADO / WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- syntax indexes [ADO], ADO/WFC
- collections [ADO], ADO/WFC syntax
- ADO/WFC syntax index [ADO]
ms.assetid: 073f9a0e-c755-42dd-9f71-4647d68e331a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e4c5a2e9ae543f7ebbbefb6286835906626a6285
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831198"
---
# <a name="collections-ado---wfc-syntax"></a>Collections (ADO/WFC-Syntax)
**Paket com.ms.wfc.data**  
  
## <a name="parameters"></a>Parameter  
  
### <a name="methods"></a>Methoden  
  
```  
public void append(com.ms.wfc.data.Parameter param)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public Parameter getItem(int n)  
public Parameter getItem(String s)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getCount()  
```  
  
## <a name="fields"></a>Felder  
  
### <a name="methods"></a>Methoden  
  
```  
public void append(String name, int type)  
public void append(String name, int type, int definedSize)  
public void append(String name, int type, int definedSize, int attrib)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public com.ms.wfc.data.Field getItem(int n)  
public com.ms.wfc.data.Field getItem(String s)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getCount()  
```  
  
## <a name="errors"></a>Fehler  
  
### <a name="methods"></a>Methoden  
  
```  
public void clear()  
public void refresh()  
public com.ms.wfc.data.Error getItem(int n)  
public com.ms.wfc.data.Error getItem(String s)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getCount()  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Errors-Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
