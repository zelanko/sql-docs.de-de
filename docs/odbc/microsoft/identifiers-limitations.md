---
description: Einschränkungen für Bezeichner
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
ms.openlocfilehash: f5efaba8fa73f61082be8d7cd8dca78626a9f972
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500343"
---
# <a name="identifiers-limitations"></a>Einschränkungen für Bezeichner
Wenn ein Bezeichner ein Leerzeichen oder ein spezielles Symbol enthält, muss der Bezeichner in backanführungs Zeichen eingeschlossen werden. Ein gültiger Name ist eine Zeichenfolge, die nicht länger als 64 Zeichen ist, deren erstes Zeichen kein Leerzeichen sein darf. Gültige Namen dürfen keine Steuerzeichen oder die folgenden Sonderzeichen enthalten: "&#124; # *? [ ] . ! $ .  
  
 Verwenden Sie die in der SQL-Grammatik aufgelisteten reservierten Wörter in Anhang C der *ODBC-Programmier Referenz* (oder Kurzform der reservierten Wörter) nicht als Bezeichner (d. h. Tabellen-oder Spaltennamen), es sei denn, Sie schließen das Wort in Anführungszeichen (') ein.
