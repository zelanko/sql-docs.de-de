---
description: get_OLEDBCommand-Methode
title: get_OLEDBCommand-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: rothja
ms.author: jroth
ms.openlocfilehash: f824359fb373b2e2ac1347d10ef5ea32e9bee091
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972821"
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
 [Iadocommandconstruction](/previous-versions/windows/desktop/aa965677(v=vs.85))