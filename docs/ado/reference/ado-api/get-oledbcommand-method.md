---
title: Get_OLEDBCommand-Methode | Microsoft-Dokumentation
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
ms.openlocfilehash: e7b2668c3693078c7027b26fa61df73b81161970
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979352"
---
# <a name="getoledbcommand-method"></a>Get_OLEDBCommand-Methode
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
 [IADOCommandConstruction](http://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
