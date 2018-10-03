---
title: Autocommit-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87a5bababd2129ffb7e0aad36a2ceb3362d4acd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792358"
---
# <a name="auto-commit-mode"></a>Autocommitmodus
*Im Autocommit-Modus* jeder Datenbankvorgang ist eine Transaktion, die ein Commit ausgeführt wird, wenn ausgeführt. Dieser Modus eignet sich für viele reale Transaktionen, die aus einer SQL-Anweisung bestehen. Es ist nicht erforderlich ist, trennen oder Abschluss dieser Transaktionen angeben. Bei Datenbanken ohne Unterstützung von Transaktionen ist die Autocommit-Modus der einzige unterstützte Modus. In solchen Datenbanken sind Anweisungen ein Commit ausgeführt, wenn sie ausgeführt werden, und es keine Möglichkeit gibt, diese zurückzusetzen; Sie sind daher immer im Autocommit Modus.  
  
 Wenn das zugrunde liegende DBMS Transaktionen mit automatischem Commit-Modus nicht unterstützt, kann der Treiber emulieren sie durch jede SQL-Anweisung manuell zu übernehmen, während der Ausführung.  
  
 Wenn ein Batch von SQL-Anweisungen in den Autocommit-Modus ausgeführt wird, sind es Daten datenquellenspezifischen, wenn Sie die Anweisungen im Batch ein Commit ausgeführt werden. Sie können ein Commit ausgeführt werden während der Ausführung oder als Ganzes nachdem der gesamte Batch ausgeführt wurde. Einige Datenquellen unterstützen möglicherweise diese beiden und möglicherweise eine Möglichkeit, einen oder anderen auszuwählen. Insbesondere wenn ein Fehler in der Mitte der Batch auftritt, ist es Daten datenquellenspezifischen, ob die bereits ausgeführten Anweisungen werden ein Commit oder Rollback. Daher sollten in interoperable Anwendungen ausführen können, die Batches verwenden, müssen ein Commit oder Rollback als Ganzes Batches nur im Manualcommit-Modus ausgeführt werden.
