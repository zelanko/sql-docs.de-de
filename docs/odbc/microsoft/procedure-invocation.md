---
title: Prozeduraufruf | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b33bc399646a6d274c875abd36d53219a2814e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200515"
---
# <a name="procedure-invocation"></a>Prozeduraufruf
Wenn die Microsoft Access-Treiber verwendet wird, können Prozeduren aus dem Treiber aufgerufen werden, mithilfe der **SQLExecDirect** oder **SQLPrepare** -Funktion mit der folgenden Syntax: {Aufrufen *Prozedurname*  [(*Parameter*[,*Parameter*]...)]}. Beachten Sie, dass Ausdrücke als Parameter an eine aufgerufene Prozedur nicht unterstützt werden.  
  
 Wenn der Name einer Prozedur, einen Bindestrich enthält, muss der Name mit Back-Anführungszeichen (') getrennt werden.  
  
 Eine parametrisierte Abfrage kann mit der vorherigen Anweisung aufgerufen werden.
