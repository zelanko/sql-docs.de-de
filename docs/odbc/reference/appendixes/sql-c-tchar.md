---
title: SQL_C_TCHAR | Microsoft Docs
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
ms.openlocfilehash: 973d94b9b47371090a5f54fd3d259854ba78e9c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304071"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
Der SQL_C_TCHAR Typbezeichner identifiziert keinen Datentyp. Es handelt sich um ein Makro, das in der Headerdatei für die Unicode-Konvertierung vorhanden ist. Je nach Einstellung des **UNICODE-#define**wird er durch SQL_C_CHAR oder SQL_C_WCHAR ersetzt. Es ist nützlich für eine Anwendung, die Zeichendaten überträgt, die sowohl als ANSI- als auch als Unicode-Anwendung kompiliert werden.
