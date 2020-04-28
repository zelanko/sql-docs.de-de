---
title: Getdataproviderdso-Methode | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932487"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO-Methode
Ruft das zugrunde liegende OLE DB Datenquellen Objekt vom Shape-Anbieter ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppdataproviderdsoiunknown*  
 vorgenommen  Ein Zeiger auf einen Zeiger, der die IUnknown des zugrunde liegenden OLE DB Datenquellen Objekts zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ruft den Schnittstellen Zeiger nicht ab. Wenn der Aufrufer den-Zeiger enthalten soll, muss der Aufrufer das erforderliche Adressat und Release ausführen.  
  
## <a name="applies-to"></a>Gilt für  
 [IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
