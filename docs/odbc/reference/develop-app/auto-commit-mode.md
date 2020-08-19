---
description: Autocommitmodus
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af4b532a2163f0c30a3bdb792cfada6bdf806c43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476892"
---
# <a name="auto-commit-mode"></a>Autocommitmodus
*Im Autocommit-Modus* ist jeder Daten Bank Vorgang eine Transaktion, für die ein Commit ausgeführt wird, wenn Sie ausgeführt wird. Dieser Modus eignet sich für viele reale Transaktionen, die aus einer einzelnen SQL-Anweisung bestehen. Es ist nicht erforderlich, den Abschluss dieser Transaktionen zu begrenzen oder anzugeben. In Datenbanken ohne Transaktionsunterstützung ist der Autocommit-Modus der einzige unterstützte Modus. In solchen Datenbanken werden für Anweisungen ein Commit ausgeführt, wenn Sie ausgeführt werden, und es gibt keine Möglichkeit, ein Rollback auszuführen. Sie befinden sich daher immer im Autocommit-Modus.  
  
 Wenn das zugrunde liegende DBMS Transaktionen im Autocommit-Modus nicht unterstützt, kann der Treiber Sie emulieren, indem er bei der Ausführung manuell einen Commit für jede SQL-Anweisung ausführt.  
  
 Wenn ein Batch von SQL-Anweisungen im Autocommit-Modus ausgeführt wird, ist er Datenquellen spezifisch, wenn für die Anweisungen im Batch ein Commit ausgeführt wird. Für Sie kann ein Commit ausgeführt werden, während Sie ausgeführt werden, oder als Ganzes, nachdem der gesamte Batch ausgeführt wurde. Einige Datenquellen unterstützen möglicherweise beide Verhaltensweisen und können eine Möglichkeit zum Auswählen eines oder der anderen darstellen. Insbesondere, wenn ein Fehler in der Mitte des Batches auftritt, ist er Datenquellen spezifisch, unabhängig davon, ob für die bereits ausgeführten Anweisungen ein Commit oder ein Rollback ausgeführt wird. Daher sollten interoperable Anwendungen, die Batches verwenden und verlangen, dass Sie als Ganzes ausgeführt werden müssen, nur im manuellen Commitmodus Batches ausführen.
