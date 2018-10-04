---
title: Behandlung großer Objekte (LOB)-Parametern in der CLR | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 6079766625633391e281b99751ba42bb772531e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848211"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Behandlung von LOB-Parametern (Large Object) in der CLR-Routine
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Verwendung **SqlBytes** und **SqlChars** großer Objekte (LOB)-binary-Typs zu übergeben (**'varbinary(max)'**) und LOB-Zeichenparameter (**nvarchar(max)**) Parameter bzw. Mithilfe dieser Parameter können die LOB-Werte von der Datenbank an die CLR-Routine (Common Language Runtime) in einem Strom übergeben werden, sodass nicht der gesamte Wert in einen verwalteten Bereich kopiert werden muss. **SqlBinary** und **SqlString** sollte nur für kleine Binärdatei- und Zeichenfolgenwerte verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
