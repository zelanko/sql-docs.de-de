---
description: put_OLEDBCommand-Methode
title: put_OLEDBCommand-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- put_OLEDBCommand method [ADO]
ms.assetid: ca6a5804-bf5c-4afc-99db-22904bc0b33d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5239a1b1924cb767d0425b2a6c686fc15607a08a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989941"
---
# <a name="put_oledbcommand-method"></a>put_OLEDBCommand-Methode
Diese Methode führt keinen Vorgang aus und gibt immer S_OK zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT put_OLEDBCommand(  
      IUnknown *pOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *poledbcommand*  
 in Zeiger auf ein OLE DB Befehls Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Iadocommandconstruction](/previous-versions/windows/desktop/aa965677(v=vs.85))