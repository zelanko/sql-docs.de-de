---
title: Data-at-Execution und Text-, ntext- oder Image-Spalten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 90777c1f7f1ac50266eaf7fe473c5ca3b1c2f189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150340"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Data-at-Execution und Text-, ntext- oder Imagespalten
  ODBC verfügt über eine Funktion namens Data-at-Execution (Daten bei Ausführung), die es Anwendungen ermöglicht, sehr große Datenmengen in gebundenen Spalten oder Parametern zu verarbeiten. Beim Abrufen sehr großer **Text**, **Ntext**, oder **Image** Spalten, eine Anwendung möglicherweise nicht einfach einen sehr umfangreichen Puffer zuzuordnen, binden Sie die Spalte im Puffer und Abrufen die Zeile. Beim Aktualisieren sehr großer **Text**, **Ntext**, oder **Image** Spalten, die Anwendung möglicherweise nicht einfach einen sehr umfangreichen Puffer zuzuordnen, binden es an eine parametermarkierung in einem SQL Anweisung, und führen Sie die Anweisung. In diesen Fällen muss die Anwendung verwenden [SQLGetData](../native-client-odbc-api/sqlgetdata.md) oder [SQLPutData](../native-client-odbc-api/sqlputdata.md) mit ihrer Data-at-Execution-Optionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text und Imagespalten](managing-text-and-image-columns.md)  
  
  