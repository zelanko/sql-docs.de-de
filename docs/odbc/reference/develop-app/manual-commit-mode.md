---
title: Manualcommit-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1952d4185c80a3b49b7742a9dba1f3d8d41a6ca6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667918"
---
# <a name="manual-commit-mode"></a>Manualcommitmodus
*Im Manualcommit-Modus* Transaktionen müssen explizit durch Aufrufen von Anwendungen abschließen **SQLEndTran** Commit zu übernehmen, oder sie Rollback. Dies ist der normale Transaktionsmodus für die meisten relationalen Datenbanken.  
  
 Transaktionen in ODBC müssen nicht explizit initiiert werden. Stattdessen startet eine Transaktion implizit, wenn die Anwendung gestartet wird, für die Datenbank ausgeführt. Wenn die Datenquelle Start einer expliziten Transaktion erforderlich ist, muss der Treiber bereitstellen, wenn die Anwendung führt eine Anweisung, die eine Transaktion erfordert und keine aktuelle Transaktion vorhanden ist.
