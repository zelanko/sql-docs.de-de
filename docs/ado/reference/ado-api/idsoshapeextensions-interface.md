---
title: Idsoshapeextensions-Schnittstelle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d49db4cb1d471d06b6e834e46218307bc25a008
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758706"
---
# <a name="idsoshapeextensions-interface"></a>IDSOShapeExtensions-Schnittstelle
Ruft das zugrunde liegende OLE DB Datenquellen Objekt für den Shape-Anbieter ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
interface IDSOShapeExtensions: public IUnknown {  
public:  
      HRESULT  GetDataProviderDSO(  
            IUnknown **ppDataProviderDSOIUnknown  
      );  
};  
```  
  
## <a name="methods"></a>Methoden  
  
|||  
|-|-|  
|[GetDataProviderDSO-Methode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Ruft das zugrunde liegende OLE DB Datenquellen Objekt vom Shape-Anbieter ab.|  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2,0 und höher  
  
 **Bibliothek:** "MSADO15. dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
