---
description: GetDataProviderDSO-Methode
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
ms.openlocfilehash: 1a45d78960b8b6b1ba2534e39f080a6c94fc0655
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443572"
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
