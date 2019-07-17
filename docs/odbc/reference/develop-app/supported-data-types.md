---
title: Unterstützte Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5ec0f3943fd52540f094a23e9b3f9f3886e1371
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114079"
---
# <a name="supported-data-types"></a>Unterstützte Datentypen
Die Datentypen, die vom DBMS unterstützt abweichen erheblich. Eine Anwendung kann bestimmen, die Namen und die Eigenschaften der unterstützten Datentypen durch Aufrufen von **SQLGetTypeInfo**. Aufgrund der großen Unterschiede in den Datentypnamen müssen die Anwendung muss den Datentypnamen zurückgegebenes verwenden **SQLGetTypeInfo** in **CREATE TABLE** Anweisungen. Weitere Informationen finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
