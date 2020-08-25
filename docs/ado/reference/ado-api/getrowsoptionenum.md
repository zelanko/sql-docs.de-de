---
description: GetRowsOptionEnum
title: GetRowsOptionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetRowsOptionEnum
helpviewer_keywords:
- GetRowsOptionEnum enumeration [ADO]
ms.assetid: adc109b9-79f4-4946-a5eb-658e22e9a8a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c071ba19a974f1ac63a31c8d01a4ed42f56804a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774939"
---
# <a name="getrowsoptionenum"></a>GetRowsOptionEnum
Gibt an, wie viele Datensätze aus einem [Recordset](./recordset-object-ado.md)abgerufen werden sollen.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adgetrowsrest**|-1|Ruft die restlichen Datensätze im **Recordset**entweder von der aktuellen Position oder einem Lesezeichen ab, das durch den *Start* -Parameter der [GetRows](./getrows-method-ado.md) -Methode angegeben wird.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. getrowsoption. Rest|  
  
## <a name="applies-to"></a>Gilt für  
 [GetRows-Methode (ADO)](./getrows-method-ado.md)