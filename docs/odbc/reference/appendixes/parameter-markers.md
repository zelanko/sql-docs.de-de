---
title: Parametermarkierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: MightyPen
ms.author: genemi
ms.reviewer: ''
manager: craigg
ms.openlocfilehash: cda6719eb46a4a05222bd54062e6cab98459d7dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181775"
---
# <a name="parameter-markers"></a>Parametermarker
Eine Anwendung kann nicht parametermarkierungen in den folgenden Speicherorten platzieren, in Übereinstimmung mit der SQL-92-Spezifikation. Eine umfassendere Liste finden Sie unter der SQL-92-Spezifikation.  
  
-   In einem **wählen** Liste  
  
-   Als *Ausdrücke* in einem *Vergleichsprädikat*  
  
-   Als beide Operanden des binären Operators  
  
-   Als die ersten und zweiten Operanden des eine **BETWEEN** Vorgang  
  
-   Als sowohl das erste und dritte Operanden ein **BETWEEN** Vorgang  
  
-   Wie die Expression-Abonnements und der erste Wert einer **IN** Vorgang  
  
-   Als Operand eines unären + oder - Vorgang  
  
-   Als Argument ein *mengenverweis-Funktion*  
  
 Weitere Informationen zu den parametermarkierungen finden Sie in der SQL-92-Spezifikation. Weitere Informationen zu Parametern finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).
