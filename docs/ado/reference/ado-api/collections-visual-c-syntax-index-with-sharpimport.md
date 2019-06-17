---
title: 'Auflistungen (Visual C++-Syntaxindex mit #import) | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9f761a0d65954e104be0849f10c786cc709085a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718248"
---
# <a name="collections-visual-c-syntax-index-with-import"></a>Auflistungen (Visual C++-Syntaxindex mit #import)
Es ist hilfreich zu wissen, dass Auflistungen bestimmte allgemeine Methoden und Eigenschaften erben.  
  
 Alle Sammlungen erben die **Anzahl** Eigenschaft und **aktualisieren** -Methode und alle Sammlungen hinzufügen der **Element** Eigenschaft. Die **Fehler** fügt der Auflistung der **löschen** Methode. Die **Parameter** Auflistung erbt die **Append** und **löschen** Methoden, während die **Felder** Auflistung fügt der **Append**, **löschen**, und **Update** Methoden.  
  
## <a name="properties-collection"></a>'Properties'-Sammlung  
  
### <a name="methods"></a>Methoden  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Errors-Collection  
  
### <a name="methods"></a>Methoden  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Parameters-Auflistung  
  
### <a name="methods"></a>Methoden  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Fields-Sammlung  
  
### <a name="methods"></a>Methoden  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Errors-Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters-Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
