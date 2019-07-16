---
title: SQLGetTypeInfo (Excel-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 227fef1ecd28e5099b599e86c82c3cc42fbacd0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898709"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME) zurückgegeben wird, in der Tabelle erzeugten **SQLGetTypeInfo** wird der Name, der am häufigsten von der Datenquelle verwendet werden.  
  
 SQL_ALL_EXCEPT_LIKE wird in der DURCHSUCHBAREN Spalte für das Byte, Leistungsindikator, Double, einzelne, lange und kurze Datentypen zurückgegeben werden. (Die LIKE-Funktion kann erreicht werden, durch Konvertieren des Werts in ein Zeichen mit der ODBC-kanonische Konvertierungsfunktionen, klicken Sie dann der Vergleich ausgeführt.)  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, werden die ODBC-Typnamen in der TYPE_NAME-Spalte, die von zurückgegeben wird zurückgegeben **SQLGetTypeInfo**.
