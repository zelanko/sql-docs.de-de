---
title: Umgang mit Parametern für große Objekte (LOB) in der CLR | Microsoft Docs
description: In diesem Artikel wird beschrieben, wie große Objektwerte (LOB) für Parameter in der SQL Server CLR-Integration behandelt werden. Verwenden Sie SqlBytes und SqlChars für LOB-Typen.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: 0941ca2f5fc1a05397dd3dbec5e0dd27c6e5d815
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488451"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Behandlung von LOB-Parametern (Large Object) in der CLR-Routine
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Verwenden Sie **SqlBytes** und **SqlChars,** um die Parameter "Large Object (LOB) binary type (**varbinary(max))**) und LOB character type (**nvarchar(max))** zu übergeben. Mithilfe dieser Parameter können die LOB-Werte von der Datenbank an die CLR-Routine (Common Language Runtime) in einem Strom übergeben werden, sodass nicht der gesamte Wert in einen verwalteten Bereich kopiert werden muss. **SqlBinary** und **SqlString** sollten nur für kleine Binär- und Zeichenfolgenwerte verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
