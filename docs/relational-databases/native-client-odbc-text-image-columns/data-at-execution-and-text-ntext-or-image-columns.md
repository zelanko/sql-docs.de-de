---
description: Data-at-Execution und Text-, ntext- oder Imagespalten
title: Data-at-Execution und Text, ntext, Image
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f0faef2097287e026023afe30c379a2f08f3d82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88381836"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Data-at-Execution und Text-, ntext- oder Imagespalten
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  ODBC verfügt über eine Funktion namens Data-at-Execution (Daten bei Ausführung), die es Anwendungen ermöglicht, sehr große Datenmengen in gebundenen Spalten oder Parametern zu verarbeiten. Beim Abrufen sehr großer **Text**-, **ntext**-oder **Image** -Spalten kann eine Anwendung möglicherweise nicht einfach einen riesigen Puffer zuordnen, die Spalte an den Puffer binden und die Zeile abrufen. Beim Aktualisieren sehr großer **Text**-, **ntext**-oder **Image** -Spalten kann die Anwendung möglicherweise nicht einfach einen riesigen Puffer zuordnen, Sie an eine Parameter Markierung in einer SQL-Anweisung binden und dann die Anweisung ausführen. In diesen Fällen muss die Anwendung [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) oder [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) mit ihren Data-at-Execution-Optionen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text und Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
