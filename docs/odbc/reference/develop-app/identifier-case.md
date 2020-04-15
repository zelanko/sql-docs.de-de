---
title: Identifier Fall | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940d96ece6b2c344fa02e0daadd6248270f4d19e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300150"
---
# <a name="identifier-case"></a>Groß-/Kleinschreibung von Bezeichnern
In SQL-Anweisungen und Katalogfunktionsargumenten können Bezeichner und in Anführungszeichen zitierte Bezeichner entweder groß sein oder nicht, was eine Anwendung bestimmen kann, indem sie **SQLGetInfo** mit den Optionen SQL_IDENTIFIER_CASE und SQL_QUOTED_IDENTIFIER_CASE aufruft.  
  
 Jede dieser Optionen verfügt über vier mögliche Rückgabewerte: eine, die angibt, dass die Groß-/Kleinschreibung des Bezeichners oder der angegebenen Bezeichner vertraulich ist, und drei, die angeben, dass sie nicht vertraulich ist. Die drei Werte, die nicht für die Groß-/Kleinschreibung berücksichtigt werden, beschreiben den Fall, in dem Bezeichner im Systemkatalog gespeichert werden. Wie Bezeichner im Systemkatalog gespeichert werden, ist nur für Anzeigezwecke relevant, z. B. wenn eine Anwendung die Ergebnisse einer Katalogfunktion anzeigt. die Groß-/Kleinschreibung von Bezeichnern wird dadurch nicht geändert.
