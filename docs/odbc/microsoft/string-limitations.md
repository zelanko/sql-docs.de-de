---
description: Einschränkungen für Zeichenfolgen
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
ms.openlocfilehash: c21d86a3c626ced52c6b7915d3cfbd9322fb596e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449132"
---
# <a name="string-limitations"></a>Einschränkungen für Zeichenfolgen
Die maximale Länge einer SQL-Anweisungs Zeichenfolge beträgt 65.000 Zeichen.  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden nur SQL-92-Zeichen folgen Konstanten (in einfachen Anführungszeichen und nicht in doppelte Anführungszeichen) unterstützt.  
  
 Der senkrechter Strich (&#124;) kann nicht in einer Zeichenfolge verwendet werden, unabhängig davon, ob das Zeichen in backanführungs Zeichen eingeschlossen ist.  
  
 Für eine maximale Interoperabilität sollten Anwendungen Zeichen folgen in Parametern übergeben, anstatt Zeichen folgen in Anführungszeichen zu übergeben.
