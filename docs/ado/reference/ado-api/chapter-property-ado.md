---
description: Chapter-Eigenschaft (ADO)
title: Chapter-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
author: rothja
ms.author: jroth
ms.openlocfilehash: ae595351ed6882bf67f543d61dc583d3350e6ce1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451012"
---
# <a name="chapter-property-ado"></a>Chapter-Eigenschaft (ADO)
Ruft ein OLE DB **Kapitel** Objekt aus/für ein [adorecordsetconstruction-Schnittstellen](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) Objekt ab oder legt es fest. Wenn Sie **put_Chapter** verwenden, um das **Kapitel** Objekt festzulegen, wird eine Teilmenge von Zeilen in ein ADO- [Recordset-Objekt](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt umgewandelt. Dadurch wird das aktuelle Kapitel des Rowsetobjekt **fest**gelegt. Dies ist eine Eigenschaft mit Lese- und Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Parameter  
 *plchapter*  
 Zeiger auf das Handle eines Kapitels.  
  
 *Lchapter*  
 Handle eines Kapitels.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaften Methode gibt die HRESULT-Standardwerte zurück, einschließlich S_OK und E_FAIL.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordsetConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
