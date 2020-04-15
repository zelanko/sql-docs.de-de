---
title: SQLGetTypeInfo (Excel-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Excel Driver
- Excel driver [ODBC], SQLGetTypeInfo
ms.assetid: 708845be-e6a1-4677-8113-c52819a43fa4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64befe30be9ed7988e0c9348e9335eb632dd975c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295070"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Excel-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erstellten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE werden in der Spalte SEARCHABLE für die Datenbyte-, Leistungs-, Doppel-, Einzel-, Lang- und Kurzdaten zurückgegeben. (Die LIKE-Funktion kann erreicht werden, indem der Wert mithilfe der kanonischen Konvertierungsfunktionen von ODBC in ein Zeichen konvertiert wird und dann der Vergleich durchgeführt wird.)  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, werden die ODBC-Typnamen in der Spalte TYPE_NAME zurückgegeben, die von **SQLGetTypeInfo**zurückgegeben wird.
