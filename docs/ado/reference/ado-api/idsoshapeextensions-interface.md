---
title: IDSOShapeExtensions-Schnittstelle | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36f91ea537b1ad2a5e52221400f41bf88dc544b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613328"
---
# <a name="idsoshapeextensions-interface"></a>IDSOShapeExtensions-Schnittstelle
Ruft das zugrunde liegende Objekt für den OLE DB-Datenquelle für das SHAPE-Anbieter ab.  
  
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
|[GetDataProviderDSO-Methode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Ruft das zugrunde liegende Objekt für den OLE DB-Datenquelle aus der Shape-Anbieter ab.|  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2.0 und höher  
  
 **Bibliothek:** "MSADO15.dll"  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
