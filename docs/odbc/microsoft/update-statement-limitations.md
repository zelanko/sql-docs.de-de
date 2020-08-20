---
description: Einschränkungen der UPDATE-Anweisung
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b7c1ea2e5e9d887005084cdb5454dcf9b5e8fa24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471399"
---
# <a name="update-statement-limitations"></a>Einschränkungen der UPDATE-Anweisung
Damit der Paradox-Treiber eine Tabelle aktualisieren kann, muss die Tabelle über einen eindeutigen Index verfügen (Paradox-Primärschlüssel). Wenn Sie den Paradox-Treiber verwenden, ohne die Datenbank-Engine "Borland" zu implementieren, ist es nicht möglich, eine Paradox-Tabelle zu aktualisieren.  
  
 Wird vom Text Treiber nicht unterstützt.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, ist es möglich, Werte zu aktualisieren, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert. Folglich wird die Update-Anweisung nicht als offiziell vom Microsoft Excel-Treiber unterstützt betrachtet. Nur die INSERT-Anweisung wird als unterstützt betrachtet.
