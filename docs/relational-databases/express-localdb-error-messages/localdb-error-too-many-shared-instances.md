---
description: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cbf03785b2da806d26fdffb863a7ddb6fb1844e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470548"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
| attribute | Wert |
| --------- | ----- |
|Produktname|SQL Server|  
|Ereignis-ID|287|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Es gibt zu viele freigegebene Instanzen, und wir können keinen eindeutigen Benutzerinstanznamen generieren. Heben Sie die Freigabe von einigen der vorhandenen freigegebenen Instanzen auf.|  
  
## <a name="explanation"></a>Erklärung  
 Es gibt zu viele freigegebene Instanzen, und wir können keinen eindeutigen Benutzerinstanznamen generieren.  
  
## <a name="user-action"></a>Benutzeraktion  
 Heben Sie die Freigabe einer oder mehrerer freigegebener lokaler Datenbanklaufzeitinstanzen auf, und versuchen Sie es erneut.  
  
  
