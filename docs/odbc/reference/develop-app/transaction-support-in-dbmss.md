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
manager: craigg
ms.openlocfilehash: 2fed5ea04e15002d31e35e25fac405a729929be8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305689"
---
# <a name="transaction-support-in-dbmss"></a>Transaktionsunterstützung in DBMS
Einige Datenbanken, insbesondere Desktopdatenbanken wie z. B. Paradox, dBASE und Btrieve, unterstützen keine Transaktionen. Selbst bei Datenbanken, die Transaktionen unterstützen, gibt es bei welche Arten von SQL-Anweisungen in einer Transaktion werden können. Weitere Informationen finden Sie unter der Option SQL_TXN_CAPABLE in die [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.
