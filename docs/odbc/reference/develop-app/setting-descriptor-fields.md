---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14724a5cc863074344cfbb02615f0ccff228f04c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447668"
---
# <a name="setting-descriptor-fields"></a>Festlegen von Deskriptorfeldern
Um die Felder der einen Deskriptor zu ändern, kann eine Anwendung aufrufen **SQLSetDescField**. Einige Felder sind schreibgeschützt und können nicht festgelegt werden. (Finden Sie unter den [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) funktionsbeschreibung.)  
  
 Aufzeichnen von deskriptorfelder festgelegt sind, mit der Nummer eines Datensatzes (*RecNumber*) 1 oder höher, While deskriptorheaderfelder mit einer Datensatz-Zahl von 0 festgelegt werden. Eine Datensatznummer 0 wird auch verwendet, um Lesezeichen-Felder, gemäß der Konvention festzulegen, die Lesezeichen in Spalte 0 enthalten sind. Dies lässt möglicherweise den Eindruck, dass Lesezeichen Felder sind in der Sicherheitsbeschreibung-Header enthalten, aber dies nicht der Fall ist. Bookmark-Felder unterscheiden sich von Headerfelder.  
  
 Wenn Sie Felder einzeln festlegen, die Anwendung sollte die Schritte im definierten [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Einige Felder festlegen, führt der Treiber auf die anderen Felder festgelegt. Dadurch wird sichergestellt, dass der Deskriptor wird immer verwendet werden, nachdem die Anwendung einen Datentyp angegeben wurde. Wenn die Anwendung das SQL_DESC_TYPE-Feld festlegt, der Treiber überprüft, ob andere Felder, die den angeben, gültig und konsistent sind.  
  
 Wenn ein Funktionsaufruf, der einem Beschreibungsfeld festlegen, würde ein Fehler auftritt, sind die Inhalte des Feldes Deskriptor nach dem Aufruf der fehlerhaften Funktion nicht definiert.
