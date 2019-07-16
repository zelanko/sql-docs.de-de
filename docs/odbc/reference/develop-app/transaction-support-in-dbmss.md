---
title: Transaktionsunterstützung in DBMS | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037633"
---
# <a name="transaction-support-in-dbmss"></a>Transaktionsunterstützung in DBMS
Einige Datenbanken, insbesondere Desktopdatenbanken wie z. B. Paradox, dBASE und Btrieve, unterstützen keine Transaktionen. Selbst bei Datenbanken, die Transaktionen unterstützen, gibt es bei welche Arten von SQL-Anweisungen in einer Transaktion werden können. Weitere Informationen finden Sie unter der Option SQL_TXN_CAPABLE in die [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.
