---
title: Einschränkungen der Update-Anweisung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1cc8cf58d4e4d826dc4b152e395dedbea395a095
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088205"
---
# <a name="update-statement-limitations"></a>Einschränkungen der UPDATE-Anweisung
Damit der Paradox-Treiber eine Tabelle aktualisieren kann, muss die Tabelle über einen eindeutigen Index verfügen (Paradox-Primärschlüssel). Wenn Sie den Paradox-Treiber verwenden, ohne die Datenbank-Engine "Borland" zu implementieren, ist es nicht möglich, eine Paradox-Tabelle zu aktualisieren.  
  
 Wird vom Text Treiber nicht unterstützt.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, ist es möglich, Werte zu aktualisieren, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert. Folglich wird die Update-Anweisung nicht als offiziell vom Microsoft Excel-Treiber unterstützt betrachtet. Nur die INSERT-Anweisung wird als unterstützt betrachtet.
