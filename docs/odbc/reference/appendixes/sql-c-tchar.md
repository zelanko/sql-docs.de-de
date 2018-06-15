---
title: SQL_C_TCHAR | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cce7467dd03210d60fad060e25885baf0df38399
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909165"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Der Typbezeichner SQL_C_TCHAR identifiziert einen-Datentyp nicht tatsächlich; Es ist ein Makro, das in die Headerdatei für Unicode-Konvertierung vorhanden ist. Sie wird von SQL_C_CHAR oder SQL_C_WCHAR ersetzt, abhängig von der Einstellung des Unicode- **#define**. Es eignet sich für eine Anwendung, die Übertragung von Zeichendaten, die als eine ANSI- und Unicode-Anwendung kompiliert werden.
