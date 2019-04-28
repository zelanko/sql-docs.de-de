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
manager: craigg
ms.openlocfilehash: 0c7d864d61d2782955a52ce6e20a7025379cc946
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028068"
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
