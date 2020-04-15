---
title: SQLGetTypeInfo (Textdateitreiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295000"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erstellten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE werden in der Spalte SEARCHABLE für die Datenbyte-, Leistungs-, Doppel-, Einzel-, Lang- und Kurzdaten zurückgegeben. (Die LIKE-Funktion kann erreicht werden, indem der Wert mithilfe der kanonischen Konvertierungsfunktionen von ODBC in ein Zeichen konvertiert wird und dann der Vergleich durchgeführt wird.)  
  
 Wenn der Texttreiber verwendet wird, gibt **SQLGetTypeInfo** einen CASE_SENSITIVE Wert von FALSE für die Textdatentypen (CHAR und LONGCHAR) zurück, wenn bei den Datentypen die Groß-/Kleinschreibung berücksichtigt wird.
