---
description: GetDataProviderDSO-Methode
title: Getdataproviderdso-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: rothja
ms.author: jroth
ms.openlocfilehash: 85e701cb7ce725aa9afa9d682467c1a97f5dd378
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972901"
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
 [IDSOShapeExtensions-Schnittstelle](./idsoshapeextensions-interface.md)