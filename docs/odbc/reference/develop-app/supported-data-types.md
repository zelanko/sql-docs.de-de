---
title: Unterstützte Datentypen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d19cde2d531819a60229dd7a780181571e169503
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307781"
---
# <a name="supported-data-types"></a>Unterstützte Datentypen
Die von DBMS unterstützten Datentypen sind sehr unterschiedlich. Eine Anwendung kann die Namen und Merkmale unterstützter Datentypen bestimmen, indem **sie SQLGetTypeInfo**aufruft. Aufgrund großer Unterschiede bei den Datentypnamen muss die Anwendung die von **SQLGetTypeInfo** in **CREATE TABLE-Anweisungen** zurückgegebenen Datentypnamen verwenden. Weitere Informationen finden Sie [unter Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
