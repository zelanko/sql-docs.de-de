---
title: UPDATE-Anweisungsbeschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ddf19c0b672901b2e778833f8bf624996d4ced3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307621"
---
# <a name="update-statement-limitations"></a>Einschränkungen der UPDATE-Anweisung
Damit der Paradox-Treiber eine Tabelle aktualisieren kann, muss die Tabelle über einen eindeutigen Index (Paradox-Primärschlüssel) verfügen. Wenn Sie den Paradox-Treiber verwenden, ohne die Borland Database Engine zu implementieren, ist es nicht möglich, eine Paradox-Tabelle zu aktualisieren.  
  
 Wird vom Texttreiber nicht unterstützt.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, ist es möglich, Werte zu aktualisieren, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert. Daher wird die UPDATE-Anweisung nicht offiziell vom Microsoft Excel-Treiber unterstützt. Nur die INSERT-Anweisung wird als unterstützt betrachtet.
