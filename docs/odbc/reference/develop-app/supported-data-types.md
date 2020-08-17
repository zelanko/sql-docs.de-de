---
description: Unterstützte Datentypen
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
ms.openlocfilehash: 349636553112449485d99fed269a43069974fccf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88385826"
---
# <a name="supported-data-types"></a>Unterstützte Datentypen
Die von DBMSs unterstützten Datentypen variieren erheblich. Eine Anwendung kann die Namen und Merkmale der unterstützten Datentypen durch Aufrufen von **SQLGetTypeInfo**ermitteln. Aufgrund der breiten Variation von Datentyp Namen muss die Anwendung die Datentyp Namen verwenden, die von **SQLGetTypeInfo** in **CREATE TABLE** -Anweisungen zurückgegeben werden. Weitere Informationen finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
