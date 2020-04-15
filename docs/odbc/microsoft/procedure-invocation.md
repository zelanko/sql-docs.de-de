---
title: Verfahrensaufruf | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290771"
---
# <a name="procedure-invocation"></a>Prozeduraufruf
Wenn der Microsoft Access-Treiber verwendet wird, können Prozeduren vom Treiber aufgerufen werden, indem die **SQLExecDirect-** oder **SQLPrepare-Funktion** mit der folgenden Syntax verwendet wird: .CALL *procedure-name* [(*parameter*[,*parameter*]...)]." Beachten Sie, dass Ausdrücke nicht als Parameter für eine aufgerufene Prozedur unterstützt werden.  
  
 Wenn ein Prozedurname einen Bindestrich enthält, muss der Name durch Rückanführungszeichen (') getrennt werden.  
  
 Eine parametrisierte Abfrage kann mit der vorherigen Anweisung aufgerufen werden.
