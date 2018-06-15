---
title: Vergleichbarkeit für ' irowsetfind ' | Microsoft Docs
description: Vergleichbarkeit für 'IRowsetFind'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1226a3e1a0177056bc38ce69cf03206be941c932
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304809"
---
# <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Für die date/time-Typen unterstützt IRowsetFind die folgenden Vergleiche:  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 Bei dem Versuch eines anderen Vergleichs wird DB_E_BADCOMPAREOP zurückgegeben. Dieses Verhalten stimmt mit der OLE DB-Spezifikation überein.  
  
## <a name="see-also"></a>Siehe auch  
 [Datum und Uhrzeit-Verbesserungen &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
