---
title: Konsistenzprüfung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edd946ca865cd9d8d2edff2c7bedbb3b2629c97c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299000"
---
# <a name="consistency-check"></a>Konsistenzprüfung
Eine Konsistenzprüfung wird vom Treiber automatisch durchgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR Feld der APD, ARD oder IPD festlegt. Wenn dieses Feld festgelegt wird, überprüft der Treiber, ob der Wert des Feldes SQL_DESC_TYPE und die Werte, die für das Feld SQL_DESC_TYPE im gleichen Datensatz gelten, gültig und konsistent sind.  
  
 Das SQL_DESC_DATA_PTR Feld einer IPD wird normalerweise nicht festgelegt. Eine Anwendung kann dies jedoch tun, um eine Konsistenzprüfung von IPD-Feldern zu erzwingen. Der Wert, auf den das SQL_DESC_DATA_PTR Feld der IPD festgelegt ist, wird nicht gespeichert und kann nicht durch einen Aufruf von **SQLGetDescField** oder **SQLGetDescRec**abgerufen werden. die Einstellung wird nur vorgenommen, um die Konsistenzprüfung zu erzwingen. Eine Konsistenzprüfung kann für eine IRD nicht durchgeführt werden.  
  
 Weitere Informationen zur Konsistenzprüfung finden Sie unter [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
