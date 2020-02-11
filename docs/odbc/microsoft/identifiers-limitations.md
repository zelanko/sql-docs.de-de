---
title: Einschränkungen für Bezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 251ae0e4e94cec903e2c4b5cf687ed9b8b41dfc8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952391"
---
# <a name="identifiers-limitations"></a>Einschränkungen für Bezeichner
Wenn ein Bezeichner ein Leerzeichen oder ein spezielles Symbol enthält, muss der Bezeichner in backanführungs Zeichen eingeschlossen werden. Ein gültiger Name ist eine Zeichenfolge, die nicht länger als 64 Zeichen ist, deren erstes Zeichen kein Leerzeichen sein darf. Gültige Namen dürfen keine Steuerzeichen oder die folgenden Sonderzeichen enthalten: "&#124; # *? [ ] . ! $ .  
  
 Verwenden Sie die in der SQL-Grammatik aufgelisteten reservierten Wörter in Anhang C der *ODBC-Programmier Referenz* (oder Kurzform der reservierten Wörter) nicht als Bezeichner (d. h. Tabellen-oder Spaltennamen), es sei denn, Sie schließen das Wort in Anführungszeichen (') ein.
