---
title: Überprüfen des Feature-Supports und der Variabilität | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47f16160c05d1c410e3889f0bb857befe88df5b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299170"
---
# <a name="checking-feature-support-and-variability"></a>Überprüfung der Funktionsunterstützung und Variabilität
Um die Funktionsunterstützung und Variabilität zu überprüfen, rufen Anwendungen im Allgemeinen **SQLGetInfo**, **SQLGetFunctions**und **SQLGetTypeInfo**auf. Ein guter Ausgangspunkt sind die API- und SQL-Grammatikkonformitätsstufen des Treibers. Diese beschreiben ein breites Maß an Feature-Unterstützung. Die Anwendung kann dann **SQLGetInfo** mit anderen Optionen aufrufen, um die Unterstützung oder Variabilität der Features **zu** bestimmen, die sie benötigt, um zu bestimmen, ob Funktionen unterstützt werden, die sie über die zurückgegebene Konformitätsebene hinaus benötigt, und **SQLGetTypeInfo,** um zu bestimmen, welche SQL-Datentypen unterstützt werden.  
  
 Eine Anwendung kann bestimmen, ob eine Anweisung oder ein Verbindungsattribut unterstützt wird, indem **SQLSetStmtAttr** oder **SQLSetConnectAttr** mit diesem Attribut aufgerufen wird. Wenn die Funktion SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, wird das Attribut unterstützt. Wenn SQL_ERROR und SQLSTATE HYC00 zurückgegeben wird (Optionales Feature nicht implementiert), wird das Attribut nicht unterstützt.  
  
 Anwendungen können auch eine begrenzte Menge an Informationen bestimmen, bevor sie eine Verbindung mit dem Treiber herstellen, indem sie **SQLDrivers**aufrufen.
