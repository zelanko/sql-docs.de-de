---
description: SQL_C_TCHAR
title: SQL_C_TCHAR | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6fc7ff6e6334d49acc4e230b5fb12feb3f85556e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483173"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
Der SQL_C_TCHAR Typbezeichner identifiziert nicht tatsächlich einen Datentyp. Es handelt sich um ein Makro, das in der Header Datei für die Unicode-Konvertierung vorhanden ist. Sie wird durch SQL_C_CHAR oder SQL_C_WCHAR ersetzt, abhängig von der Einstellung der Unicode- **#define**. Es ist nützlich für eine Anwendung, die Zeichendaten überträgt, die als ANSI-und Unicode-Anwendung kompiliert werden.
