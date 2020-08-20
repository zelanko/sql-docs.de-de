---
description: Setup-DLL-API-Referenz
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5cb3e20a1c25d206a1dd27367bbe4a128af0818f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487333"
---
# <a name="setup-dll-api-reference"></a>Setup-DLL-API-Referenz
In diesem Abschnitt wird die Syntax der Treiber-Setup-DLL-API beschrieben, die aus zwei Funktionen besteht (**ConfigDriver** und **ConfigDSN**). **ConfigDriver** und **ConfigDSN** können sich entweder in der Treiber-DLL oder in einer separaten Setup-DLL befinden.  
  
 Außerdem wird in diesem Abschnitt die Syntax der-Konvertierungs-DLL-API beschrieben, die aus einer einzelnen Funktion (**ConfigTranslator**) besteht. **ConfigTranslator** kann sich entweder in der Konvertierungs-DLL oder in einer separaten Setup-DLL befinden.  
  
 Jede Funktion wird mit der Version von ODBC bezeichnet, in der Sie eingeführt wurde.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ConfigDriver-Funktion](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator-Funktion](../../../odbc/reference/syntax/configtranslator-function.md)
