---
title: Verarbeiten von Batches von SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], batches
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], batches
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- SQL statements [ODBC], batches
- batches [ODBC], processing batches of SQL statements
ms.assetid: 04b93ef9-11de-47a3-8bd8-ba963c42f182
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f952b21267b73c7ae508f46d896dbfdbb4160e20
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100569"
---
# <a name="processing-batches-of-sql-statements"></a>Verarbeiten von Batches von SQL-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die Cursorbibliothek unterstützt keine Batches von SQL-Anweisungen, z. B. SQL-Anweisungen, die für die das Anweisungsattribut verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist. Wenn eine Anwendung einen Batch mit SQL-Anweisungen an die Cursorbibliothek übermittelt werden, sind die Ergebnisse nicht definiert.
