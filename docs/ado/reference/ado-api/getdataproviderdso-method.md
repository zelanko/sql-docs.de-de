---
title: GetDataProviderDSO-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2b5fbe59ab58b31cd0b796cbe46963683aa890b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932487"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO-Methode
Ruft das zugrunde liegende Objekt für den OLE DB-Datenquelle aus der Shape-Anbieter ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppDataProviderDSOIUnknown*  
 [out]  Ein Zeiger auf einen Zeiger, der die IUnknown-Äquivalent der das zugrunde liegende Objekt für den OLE DB-Datenquelle zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht "AddRef" den Schnittstellenzeiger auf. Möchte, dass der Aufrufer den Zeiger zu halten, der Aufrufer müssen die erforderlichen Addref und release.  
  
## <a name="applies-to"></a>Betrifft  
 [IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
