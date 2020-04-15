---
title: SQLGetTypeInfo (Paradox-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 693441c088865be85b18106a4c769a9f3f676f13
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295100"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält paradox driverspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erstellten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE werden in der Spalte SEARCHABLE für die Datenbyte-, Leistungs-, Doppel-, Einzel-, Lang- und Kurzdaten zurückgegeben. (Die LIKE-Funktion kann erreicht werden, indem der Wert mithilfe der kanonischen Konvertierungsfunktionen von ODBC in ein Zeichen konvertiert und anschließend der Vergleich durchgeführt wird.)
