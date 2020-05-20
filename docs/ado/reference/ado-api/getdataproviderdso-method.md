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
author: rothja
ms.author: jroth
ms.openlocfilehash: 55272fdbcd0aacfc8e98cb4e38ae19270b3b461a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760046"
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
  
## <a name="applies-to"></a>Gilt für:  
 [IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
