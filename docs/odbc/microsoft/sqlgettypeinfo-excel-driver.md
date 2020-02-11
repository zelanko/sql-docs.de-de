---
title: Sqlgettypeingefo (Excel-Treiber) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898709"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erzeugten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE wird in der durchsuchbaren Spalte für die Datentypen "Byte", "Counter", "Double", "Long" und "Short" zurückgegeben. (Die like-Funktion kann durch das Konvertieren des Werts in ein Zeichen mithilfe der kanonischen ODBC-Konvertierungs Funktionen und anschließendes durchführen des Vergleichs erreicht werden.)  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, werden die ODBC-Typnamen in der von **SQLGetTypeInfo**zurückgegebenen TYPE_NAME Spalte zurückgegeben.
