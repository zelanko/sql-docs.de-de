---
title: DLL-API-Referenz einrichten | Microsoft Docs
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
ms.openlocfilehash: 25cff50b73868b5b3015dfc1a00c560c344a6d36
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298885"
---
# <a name="setup-dll-api-reference"></a>Setup-DLL-API-Referenz
In diesem Abschnitt wird die Syntax der Treibereinrichtungs-DLL-API beschrieben, die aus zwei Funktionen besteht (**ConfigDriver** und **ConfigDSN**). **ConfigDriver** und **ConfigDSN** können sich entweder in der Treiber-DLL oder in einer separaten Setup-DLL befinden.  
  
 Darüber hinaus beschreibt dieser Abschnitt die Syntax der Translator Setup DLL API, die aus einer einzelnen Funktion besteht (**ConfigTranslator**). **ConfigTranslator** kann sich entweder in der Übersetzer-DLL oder in einer separaten Setup-DLL befinden.  
  
 Jede Funktion ist mit der Version von ODBC beschriftet, in der sie eingeführt wurde.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ConfigDriver-Funktion](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator-Funktion](../../../odbc/reference/syntax/configtranslator-function.md)
