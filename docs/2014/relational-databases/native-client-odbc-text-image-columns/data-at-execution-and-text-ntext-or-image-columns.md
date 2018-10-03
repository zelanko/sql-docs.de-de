---
title: Data-at-Execution und Text-, ntext- oder Image-Spalten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076731"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Data-at-Execution und Text-, ntext- oder Imagespalten
  ODBC verfügt über eine Funktion namens Data-at-Execution (Daten bei Ausführung), die es Anwendungen ermöglicht, sehr große Datenmengen in gebundenen Spalten oder Parametern zu verarbeiten. Beim Abrufen sehr großer **Text**, **Ntext**, oder **Image** Spalten, eine Anwendung möglicherweise nicht einfach einen sehr umfangreichen Puffer zuzuordnen, binden Sie die Spalte in den Puffer und Abrufen die Zeile. Beim Aktualisieren sehr großer **Text**, **Ntext**, oder **Image** Spalten, die Anwendung möglicherweise nicht einfach einen sehr umfangreichen Puffer zuzuordnen, binden es an eine parametermarkierung in einer SQL -Anweisung, und führen Sie die Anweisung. In diesen Fällen muss die Anwendung mithilfe [SQLGetData](../native-client-odbc-api/sqlgetdata.md) oder [SQLPutData](../native-client-odbc-api/sqlputdata.md) mit der Data-at-Execution-Optionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text und Imagespalten](managing-text-and-image-columns.md)  
  
  
