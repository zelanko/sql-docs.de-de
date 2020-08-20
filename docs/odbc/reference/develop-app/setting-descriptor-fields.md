---
description: Festlegen von Deskriptorfeldern
title: Festlegen von Deskriptorfeldern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6625db69709098f3a3db1a1d40f9ab583eee4030
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476432"
---
# <a name="setting-descriptor-fields"></a>Festlegen von Deskriptorfeldern
Zum Ändern der Felder eines Deskriptors kann eine Anwendung **SQLSetDescField**aufrufen. Einige Felder sind schreibgeschützt und können nicht festgelegt werden. (Weitere Informationen finden Sie in der Beschreibung der [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) -Funktion.)  
  
 Deskriptordatensatz-Felder werden mit einer Datensatznummer (*RecNumber*) von 1 oder höher festgelegt, während Deskriptorheaderfelder mit einer Datensatznummer von 0 festgelegt werden. Eine Datensatznummer von 0 wird auch verwendet, um Lesezeichen Felder in Übereinstimmung mit der Konvention festzulegen, dass Lesezeichen in Spalte 0 enthalten sind. Dadurch wird möglicherweise der Eindruck hinterlassen, dass Lesezeichen Felder im deskriptorheader enthalten sind, dies ist jedoch nicht der Fall. Lesezeichen Felder unterscheiden sich von Header Feldern.  
  
 Wenn Felder einzeln festgelegt werden, sollte die Anwendung der in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)definierten Sequenz folgen. Das Festlegen einiger Felder bewirkt, dass der Treiber andere Felder festlegt. Dadurch wird sichergestellt, dass der Deskriptor immer einsatzbereit ist, sobald die Anwendung einen Datentyp angegeben hat. Wenn die Anwendung das SQL_DESC_TYPE-Feld festlegt, prüft der Treiber, ob andere Felder, die den Typ angeben, gültig und konsistent sind.  
  
 Wenn ein Funktions Aufrufwert, der ein Deskriptorfeld festgelegt hätte, fehlschlägt, ist der Inhalt des deskriptorfelds nach dem fehlgeschlagenen Funktions Versuch nicht definiert.
