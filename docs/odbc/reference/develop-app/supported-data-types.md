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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d19cde2d531819a60229dd7a780181571e169503
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307781"
---
# <a name="supported-data-types"></a>Unterstützte Datentypen
Die von DBMSs unterstützten Datentypen variieren erheblich. Eine Anwendung kann die Namen und Merkmale der unterstützten Datentypen durch Aufrufen von **SQLGetTypeInfo**ermitteln. Aufgrund der breiten Variation von Datentyp Namen muss die Anwendung die Datentyp Namen verwenden, die von **SQLGetTypeInfo** in **CREATE TABLE** -Anweisungen zurückgegeben werden. Weitere Informationen finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
