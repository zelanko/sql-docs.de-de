---
title: Transaktionsunterstützung in DBMSs | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298005"
---
# <a name="transaction-support-in-dbmss"></a>Transaktionsunterstützung in DBMS
Einige Datenbanken, insbesondere Desktop Datenbanken wie dBase, Paradox und Btrieve, unterstützen keine Transaktionen. Auch bei Datenbanken, die Transaktionen unterstützen, gibt es Abweichungen in den Arten von SQL-Anweisungen, die in einer Transaktion auftreten können. Weitere Informationen finden Sie unter der Option SQL_TXN_CAPABLE in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.
