---
title: Einschränkungen für Zeichen folgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306061"
---
# <a name="string-limitations"></a>Einschränkungen für Zeichenfolgen
Die maximale Länge einer SQL-Anweisungs Zeichenfolge beträgt 65.000 Zeichen.  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden nur SQL-92-Zeichen folgen Konstanten (in einfachen Anführungszeichen und nicht in doppelte Anführungszeichen) unterstützt.  
  
 Der senkrechter Strich (&#124;) kann nicht in einer Zeichenfolge verwendet werden, unabhängig davon, ob das Zeichen in backanführungs Zeichen eingeschlossen ist.  
  
 Für eine maximale Interoperabilität sollten Anwendungen Zeichen folgen in Parametern übergeben, anstatt Zeichen folgen in Anführungszeichen zu übergeben.
