---
title: Generieren von NULL-Werten mithilfe von XSINIL | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie XML-Elemente für NULL-Werte mithilfe des XSINIL-Parameters in der ELEMENTS-Direkte generieren.
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 7cf18eb7c5dea9a61988533205a3a64ab1ae3fd0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85638950"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Generieren von NULL-Werten mithilfe des XSINIL-Parameters

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Von der **ELEMENTS** -Direktive wird XML konstruiert, in der jede Spalte zu einem Element im XML-Code zugeordnet wird. Wenn der Spaltenwert NULL ist, wird standardmäßig kein Element hinzugefügt. Doch durch Angeben des optionalen Parameters **XSINIL** für die ELEMENTS-Direktive können Sie anfordern, dass auch für den NULL-Wert ein Element erstellt wird. In diesem Fall wird für ein Element das **xsi:nil** -Attribut, das auf TRUE festgelegt ist, für jeden NULL-Spaltenwert zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen

[Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

[SELECT – FOR-Klausel](../../t-sql/queries/select-for-clause-transact-sql.md)
