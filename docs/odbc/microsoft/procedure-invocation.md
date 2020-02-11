---
title: Prozedur Aufruf | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070496"
---
# <a name="procedure-invocation"></a>Prozeduraufruf
Wenn der Microsoft Access-Treiber verwendet wird, können Prozeduren mithilfe der **SQLExecDirect** -Funktion oder der **SQLPrepare** -Funktion mit der folgenden Syntax aufgerufen werden: {Aufruf *Prozedur Name* [(*Parameter*[,*Parameter*]...)]}. Beachten Sie, dass Ausdrücke nicht als Parameter für eine aufgerufene Prozedur unterstützt werden.  
  
 Wenn ein Prozedur Name einen Bindestrich enthält, muss der Name mit backanführungs Zeichen (') getrennt werden.  
  
 Eine parametrisierte Abfrage kann mithilfe der vorherigen Anweisung aufgerufen werden.
