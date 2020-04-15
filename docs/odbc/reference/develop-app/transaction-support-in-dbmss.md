---
title: Transaktionsunterstützung in DBMS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6da6fdc819d8852aadcd7b672ef06e99d46c0ea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298005"
---
# <a name="transaction-support-in-dbmss"></a>Transaktionsunterstützung in DBMS
Einige Datenbanken, insbesondere Desktopdatenbanken wie dBASE, Paradox und Btrieve, unterstützen keine Transaktionen. Selbst unter Datenbanken, die Transaktionen unterstützen, gibt es Unterschiede in der Art von SQL-Anweisungen in einer Transaktion sein können. Weitere Informationen finden Sie in der Option SQL_TXN_CAPABLE in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
