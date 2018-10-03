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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744068"
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
  
## <a name="applies-to"></a>Gilt für  
 [IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
