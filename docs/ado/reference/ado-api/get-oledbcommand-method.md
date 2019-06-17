---
title: Get_OLEDBCommand-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0416ea7890b3afd430dfd1892cdfc3cd03ca3cfa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694866"
---
# <a name="getoledbcommand-method"></a>get_OLEDBCommand-Methode
Gibt den zugrunde liegenden OLE DB-Befehl, Weitergabe zuerst alle Parameterinformationen, legen Sie für die ADO-Befehl aus, um den OLE DB-Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppOLEDBCommand*  
 [out] Ein Zeiger auf einen Zeiger-Speicherort, in dem der IUnknown-Zeiger für den zugrunde liegenden OLE DB-Befehl geschrieben wird.  
  
## <a name="applies-to"></a>Gilt für  
 [IADOCommandConstruction](https://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
