---
description: get_OLEDBCommand-Methode
title: get_OLEDBCommand-Methode | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 562b10fa67b04926e512833248c99ecb7b55a1fd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443602"
---
# <a name="get_oledbcommand-method"></a>get_OLEDBCommand-Methode
Gibt den zugrunde liegenden OLE DB-Befehl zurück, wobei zuerst alle Parameterinformationen, die für den ADO-Befehl festgelegt wurden, an den OLE DB-Befehl  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppoledbcommand*  
 vorgenommen Ein Zeiger auf einen Zeiger Speicherort, an dem der IUnknown-Zeiger für den zugrunde liegenden OLE DB Befehl geschrieben wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Iadocommandconstruction](https://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
