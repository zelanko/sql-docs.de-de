---
description: SQLGetTypeInfo (Textdateitreiber)
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
ms.openlocfilehash: 1c023c4b18cd335f562541ad10885546f2163d10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449162"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (Textdateitreiber)
> [!NOTE]  
>  In diesem Thema werden Treiber spezifische Informationen zu Textdateien bereitstellt. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erzeugten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE wird in der durchsuchbaren Spalte für die Datentypen "Byte", "Counter", "Double", "Long" und "Short" zurückgegeben. (Die like-Funktion kann durch das Konvertieren des Werts in ein Zeichen mithilfe der kanonischen ODBC-Konvertierungs Funktionen und anschließendes durchführen des Vergleichs erreicht werden.)  
  
 Wenn der Text Treiber verwendet wird, gibt **SQLGetTypeInfo** den CASE_SENSITIVE Wert false für die Text Datentypen (char und LONGCHAR) zurück, wenn bei den Datentypen tatsächlich die Groß-/Kleinschreibung beachtet wird.
