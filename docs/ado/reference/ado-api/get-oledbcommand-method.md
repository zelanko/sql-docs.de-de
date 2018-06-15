---
title: Get_OLEDBCommand Methode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ec269e224dd87d430993e57b89c56a8701da407
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278697"
---
# <a name="getoledbcommand-method"></a>Get_OLEDBCommand-Methode
Gibt den zugrunde liegenden OLE DB-Befehl, weitergeben zuerst alle Parameterinformationen für den ADO-Befehl an den OLE DB-Befehl festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppOLEDBCommand*  
 [out] Ein Zeiger auf einen Zeiger Speicherort, in dem der IUnknown-Zeiger für den zugrunde liegenden OLE DB-Befehl geschrieben wird.  
  
## <a name="applies-to"></a>Gilt für  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
