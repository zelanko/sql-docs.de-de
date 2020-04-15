---
title: SQLGetTypeInfo (Zugriffstreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddfa9bd29f0834adf1c211f9b8a111db0b94d3fe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295150"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Der Name des Typs (TYPE_NAME), der in der von **SQLGetTypeInfo** erstellten Tabelle zurückgegeben wird, ist der Name, der am häufigsten von der Datenquelle verwendet wird.  
  
 SQL_ALL_EXCEPT_LIKE werden in der Spalte SEARCHABLE für die Datenbyte-, Leistungs-, Doppel-, Einzel-, Lang- und Kurzdaten zurückgegeben. (Die LIKE-Funktion kann erreicht werden, indem der Wert mithilfe der kanonischen Konvertierungsfunktionen von ODBC in ein Zeichen konvertiert wird und dann der Vergleich durchgeführt wird.)
