---
title: Auto-Commit-Modus | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f19053eec7a48eba7a51425b01744f3acd10015
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285110"
---
# <a name="auto-commit-mode"></a>Autocommitmodus
*Im Autocommit-Modus* ist jeder Datenbankvorgang eine Transaktion, die beim Ausgeführten festgeschrieben wird. Dieser Modus eignet sich für viele reale Transaktionen, die aus einer einzelnen SQL-Anweisung bestehen. Es ist nicht erforderlich, den Abschluss dieser Transaktionen abzugrenzen oder anzugeben. In Datenbanken ohne Transaktionsunterstützung ist der Autocommit-Modus der einzige unterstützte Modus. In solchen Datenbanken werden Anweisungen festgeschrieben, wenn sie ausgeführt werden, und es gibt keine Möglichkeit, sie zurückzusetzen. sie befinden sich daher immer im Auto-Commit-Modus.  
  
 Wenn das zugrunde liegende DBMS keine Autocommit-Modustransaktionen unterstützt, kann der Treiber diese emulieren, indem er jede SQL-Anweisung während der Ausführung manuell feststellt.  
  
 Wenn ein Batch von SQL-Anweisungen im AutoCommit-Modus ausgeführt wird, ist er datenquellenspezifisch, wenn die Anweisungen im Batch festgeschrieben werden. Sie können festgeschrieben werden, wenn sie ausgeführt werden oder als Ganzes, nachdem der gesamte Batch ausgeführt wurde. Einige Datenquellen unterstützen möglicherweise beide Verhaltensweisen und bieten eine Möglichkeit, eine oder die anderen auszuwählen. Insbesondere wenn ein Fehler in der Mitte des Batches auftritt, ist es datenquellenspezifisch, ob die bereits ausgeführten Anweisungen festgeschrieben oder zurückgesetzt werden. Daher sollten interoperable Anwendungen, die Batches verwenden und deren Festschreibung oder Rollback als Ganzes erfordern, Batches nur im manuellen Commit-Modus ausführen.
