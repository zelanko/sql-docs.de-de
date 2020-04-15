---
title: Festlegen von Deskriptorfeldern | Microsoft Docs
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
ms.openlocfilehash: 04f9520e2ef462df481bb104e389aeb57b5dd457
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304151"
---
# <a name="setting-descriptor-fields"></a>Festlegen von Deskriptorfeldern
Um die Felder eines Deskriptors zu ändern, kann eine Anwendung **SQLSetDescField**aufrufen. Einige Felder sind schreibgeschützt und können nicht festgelegt werden. (Siehe [sqlSetDescField-Funktionsbeschreibung.)](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Deskriptor-Datensatzfelder werden mit einer Datensatznummer (*RecNumber*) von 1 oder höher festgelegt, während Deskriptorheaderfelder mit der Datensatznummer 0 festgelegt werden. Eine Datensatznummer von 0 wird auch verwendet, um Lesezeichenfelder festzulegen, entsprechend der Konvention, dass Lesezeichen in Spalte 0 enthalten sind. Dies kann den Eindruck hinterlassen, dass Lesezeichenfelder im Deskriptorkopf enthalten sind, dies ist jedoch nicht der Fall. Lesezeichenfelder unterscheiden sich von Kopfzeilenfeldern.  
  
 Wenn Sie Felder einzeln festlegen, sollte die Anwendung der in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)definierten Sequenz folgen. Wenn Sie einige Felder festlegen, muss der Treiber andere Felder festlegen. Dadurch wird sichergestellt, dass der Deskriptor immer einsatzbereit ist, sobald die Anwendung einen Datentyp angegeben hat. Wenn die Anwendung das Feld SQL_DESC_TYPE festlegt, überprüft der Treiber, ob andere Felder, die den Typ angeben, gültig und konsistent sind.  
  
 Wenn ein Funktionsaufruf, der ein Deskriptorfeld festlegen würde, fehlschlägt, ist der Inhalt des Deskriptorfelds nach dem fehlgeschlagenen Funktionsaufruf nicht definiert.
