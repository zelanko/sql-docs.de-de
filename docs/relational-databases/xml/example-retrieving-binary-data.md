---
title: 'Beispiel: Abrufen von Binärdaten | Microsoft-Dokumentation'
description: Hier finden Sie ein Beispiel für eine SQL-Abfrage, bei der Binärdaten mithilfe der Optionen RAW und BINARY BASE64 mit der FOR XML-Klausel abgerufen werden.
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: RothJa
ms.author: jroth
ms.openlocfilehash: 08010e294b1b143c941774912d661a53c021a6ab
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632783"
---
# <a name="example-retrieving-binary-data"></a>Beispiel: Abrufen von Binärdaten

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Die folgende Abfrage gibt das Produktfoto zurück, das in einer Spalte des **varbinary(max)** -Typs gespeichert ist. Durch die Angabe der Option `BINARY BASE64` in der Abfrage werden die Binärdaten im Base64-codierten Format zurückgegeben.

## <a name="example"></a>Beispiel

```sql
USE AdventureWorks2012;
GO
SELECT ProductPhotoID, ThumbNailPhoto
FROM Production.ProductPhoto
WHERE ProductPhotoID=1
FOR XML RAW, BINARY BASE64 ;
GO
```

Erwarten Sie Folgendes Ergebnis:

```console
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)
