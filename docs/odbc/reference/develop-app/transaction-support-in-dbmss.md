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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72353e9917996ecacdc5971b4a11f9c73718ba43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037633"
---
# <a name="transaction-support-in-dbmss"></a>Transaktionsunterstützung in DBMS
Einige Datenbanken, insbesondere Desktop Datenbanken wie dBase, Paradox und Btrieve, unterstützen keine Transaktionen. Auch bei Datenbanken, die Transaktionen unterstützen, gibt es Abweichungen in den Arten von SQL-Anweisungen, die in einer Transaktion auftreten können. Weitere Informationen finden Sie unter der Option SQL_TXN_CAPABLE in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.
