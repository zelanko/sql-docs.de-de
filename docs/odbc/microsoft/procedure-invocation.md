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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32617cdb753f5fc1b9c52520cb609d2902137b54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290771"
---
# <a name="procedure-invocation"></a>Prozeduraufruf
Wenn der Microsoft Access-Treiber verwendet wird, können Prozeduren mithilfe der **SQLExecDirect** -Funktion oder der **SQLPrepare** -Funktion mit der folgenden Syntax aufgerufen werden: {Aufruf *Prozedur Name* [(*Parameter*[,*Parameter*]...)]}. Beachten Sie, dass Ausdrücke nicht als Parameter für eine aufgerufene Prozedur unterstützt werden.  
  
 Wenn ein Prozedur Name einen Bindestrich enthält, muss der Name mit backanführungs Zeichen (') getrennt werden.  
  
 Eine parametrisierte Abfrage kann mithilfe der vorherigen Anweisung aufgerufen werden.
