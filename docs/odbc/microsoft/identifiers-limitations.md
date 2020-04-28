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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7154f2db09b69e6376b1fe3af1de3f2c646ee94e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286250"
---
# <a name="identifiers-limitations"></a>Einschränkungen für Bezeichner
Wenn ein Bezeichner ein Leerzeichen oder ein spezielles Symbol enthält, muss der Bezeichner in backanführungs Zeichen eingeschlossen werden. Ein gültiger Name ist eine Zeichenfolge, die nicht länger als 64 Zeichen ist, deren erstes Zeichen kein Leerzeichen sein darf. Gültige Namen dürfen keine Steuerzeichen oder die folgenden Sonderzeichen enthalten: "&#124; # *? [ ] . ! $ .  
  
 Verwenden Sie die in der SQL-Grammatik aufgelisteten reservierten Wörter in Anhang C der *ODBC-Programmier Referenz* (oder Kurzform der reservierten Wörter) nicht als Bezeichner (d. h. Tabellen-oder Spaltennamen), es sei denn, Sie schließen das Wort in Anführungszeichen (') ein.
