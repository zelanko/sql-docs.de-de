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
ms.openlocfilehash: bc37ef6d268dba71f8270909ea9c5b938ef3ee75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070496"
---
# <a name="procedure-invocation"></a>Prozeduraufruf
Wenn die Microsoft Access-Treiber verwendet wird, können Prozeduren aus dem Treiber aufgerufen werden, mithilfe der **SQLExecDirect** oder **SQLPrepare** -Funktion mit der folgenden Syntax: {Aufrufen *Prozedurname*  [(*Parameter*[,*Parameter*]...)]}. Beachten Sie, dass Ausdrücke als Parameter an eine aufgerufene Prozedur nicht unterstützt werden.  
  
 Wenn der Name einer Prozedur, einen Bindestrich enthält, muss der Name mit Back-Anführungszeichen (') getrennt werden.  
  
 Eine parametrisierte Abfrage kann mit der vorherigen Anweisung aufgerufen werden.
