---
description: Collections (ADO/WFC-Syntax)
title: Collections (ADO-WFC-Syntax) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a3a52b1dabc9ebfa01b29e1a026214a3a97aa3f2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776199"
---
# <a name="collections-ado---wfc-syntax"></a>Collections (ADO/WFC-Syntax)
**Paket "com. ms. wfc. Data"**  
  
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
  
## <a name="errors"></a>Errors  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehlersammlung (ADO)](./errors-collection-ado.md)   
 [Fields-Auflistung (ADO)](./fields-collection-ado.md)   
 [Parameters-Collection (ADO)](./parameters-collection-ado.md)