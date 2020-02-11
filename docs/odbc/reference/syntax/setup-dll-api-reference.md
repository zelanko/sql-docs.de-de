---
title: Setup-DLL-API-Referenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26e5c36b41f68627a634714cfa06525c99451450
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947056"
---
# <a name="setup-dll-api-reference"></a>Setup-DLL-API-Referenz
In diesem Abschnitt wird die Syntax der Treiber-Setup-DLL-API beschrieben, die aus zwei Funktionen besteht (**ConfigDriver** und **ConfigDSN**). **ConfigDriver** und **ConfigDSN** können sich entweder in der Treiber-DLL oder in einer separaten Setup-DLL befinden.  
  
 Außerdem wird in diesem Abschnitt die Syntax der-Konvertierungs-DLL-API beschrieben, die aus einer einzelnen Funktion (**ConfigTranslator**) besteht. **ConfigTranslator** kann sich entweder in der Konvertierungs-DLL oder in einer separaten Setup-DLL befinden.  
  
 Jede Funktion wird mit der Version von ODBC bezeichnet, in der Sie eingeführt wurde.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [ConfigDriver-Funktion](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator-Funktion](../../../odbc/reference/syntax/configtranslator-function.md)
