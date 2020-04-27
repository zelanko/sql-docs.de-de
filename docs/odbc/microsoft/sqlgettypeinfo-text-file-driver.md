---
title: SQLGetTypeInfo (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b70b58e4760959db102450b5f8b7beed042df95
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "81295000"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (Textdateitreiber)
> [!NOTE]  
>  In diesem Thema werden Treiber spezifische Informationen zu Textdateien bereitstellt. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erzeugten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE wird in der durchsuchbaren Spalte für die Datentypen "Byte", "Counter", "Double", "Long" und "Short" zurückgegeben. (Die like-Funktion kann durch das Konvertieren des Werts in ein Zeichen mithilfe der kanonischen ODBC-Konvertierungs Funktionen und anschließendes durchführen des Vergleichs erreicht werden.)  
  
 Wenn der Text Treiber verwendet wird, gibt **SQLGetTypeInfo** den CASE_SENSITIVE Wert false für die Text Datentypen (char und LONGCHAR) zurück, wenn bei den Datentypen tatsächlich die Groß-/Kleinschreibung beachtet wird.
