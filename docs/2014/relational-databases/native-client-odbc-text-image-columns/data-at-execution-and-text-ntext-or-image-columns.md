---
title: Data-at-Execution-und Text-, ntext-oder image-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7c57cf6444e5833b6deee0dcae36d71b7a6430
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63195127"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Data-at-Execution und Text-, ntext- oder Imagespalten
  ODBC verfügt über eine Funktion namens Data-at-Execution (Daten bei Ausführung), die es Anwendungen ermöglicht, sehr große Datenmengen in gebundenen Spalten oder Parametern zu verarbeiten. Beim Abrufen sehr großer **Text**-, **ntext**-oder **Image** -Spalten kann eine Anwendung möglicherweise nicht einfach einen riesigen Puffer zuordnen, die Spalte an den Puffer binden und die Zeile abrufen. Beim Aktualisieren sehr großer **Text**-, **ntext**-oder **Image** -Spalten kann die Anwendung möglicherweise nicht einfach einen riesigen Puffer zuordnen, Sie an eine Parameter Markierung in einer SQL-Anweisung binden und dann die Anweisung ausführen. In diesen Fällen muss die Anwendung [SQLGetData](../native-client-odbc-api/sqlgetdata.md) oder [SQLPutData](../native-client-odbc-api/sqlputdata.md) mit ihren Data-at-Execution-Optionen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text und Imagespalten](managing-text-and-image-columns.md)  
  
  
