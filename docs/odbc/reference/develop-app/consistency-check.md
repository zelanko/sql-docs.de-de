---
title: Konsistenzprüfung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 419e338a5e96821606dc26a53a4fccecbc72ae3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125543"
---
# <a name="consistency-check"></a>Konsistenzprüfung
Vom Treiber wird automatisch eine Konsistenzprüfung durchgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld der APD, der ARD oder der IPD festlegt. Wenn dieses Feld festgelegt ist, überprüft der Treiber, ob der Wert des SQL_DESC_TYPE Felds und die Werte, die für das SQL_DESC_TYPE Feld im selben Datensatz gelten, gültig und konsistent sind.  
  
 Das SQL_DESC_DATA_PTR-Feld einer IPD wird normalerweise nicht festgelegt. Allerdings kann eine Anwendung dies tun, um eine Konsistenzprüfung von IPD-Feldern zu erzwingen. Der Wert, auf den das SQL_DESC_DATA_PTR-Feld der IPD festgelegt ist, wird nicht tatsächlich gespeichert und kann nicht durch einen **SQLGetDescField** -oder **SQLGetDescRec**-Befehl abgerufen werden. die Einstellung wird nur zum Erzwingen der Konsistenzprüfung durchgeführt. Eine Konsistenzprüfung kann nicht für einen IRD ausgeführt werden.  
  
 Weitere Informationen zur Konsistenzprüfung finden Sie unter [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
