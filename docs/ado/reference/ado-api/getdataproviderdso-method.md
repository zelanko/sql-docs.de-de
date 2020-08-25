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
ms.openlocfilehash: e21e45d72cd5140c542fb6d6d0b150c414fb9832
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775069"
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
 [IDSOShapeExtensions-Schnittstelle](./idsoshapeextensions-interface.md)