---
title: Überprüfung der Projektkonsistenz | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: cb73d8a4de482f24eae5794232019af9890e3624
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727788"
---
# <a name="consistency-check"></a>Konsistenzprüfung
Eine konsistenzprüfung wird automatisch vom Treiber ausgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld des APD, ARD oder IPD festlegt. Wenn dieses Feld festgelegt ist, überprüft der Treiber an, dass der Wert das SQL_DESC_TYPE-Feld und die Werte für das SQL_DESC_TYPE-Feld in den gleichen Datensatz sind gültig und konsistent.  
  
 Das SQL_DESC_DATA_PTR-Feld von einem IPD ist normalerweise nicht festgelegt. Allerdings kann eine Anwendung durchführen, um eine konsistenzprüfung des IPD-Feldern zu erzwingen können. Der Wert, der das SQL_DESC_DATA_PTR-Feld des IPD festgelegt ist, werden nicht tatsächlich gespeichert und kann nicht abgerufen werden, durch einen Aufruf von **SQLGetDescField** oder **SQLGetDescRec**; die Einstellung erfolgt nur für das Erzwingen der die konsistenzprüfung. Eine konsistenzprüfung kann nicht auf eine IRD ausgeführt werden.  
  
 Weitere Informationen zu der konsistenzprüfung, finden Sie unter [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
