---
title: Manueller Commit-Modus | Microsoft-Dokumentation
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
ms.openlocfilehash: 7189a0586ba4f62091d5eb209a56931627bc6f7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036399"
---
# <a name="manual-commit-mode"></a>Manualcommitmodus
*Im manuellen Commitmodus* müssen Anwendungen die Transaktionen explizit vervollständigen, indem Sie **SQLEndTran** aufrufen, um Sie zu committen oder einen Rollback auszuführen. Dies ist der normale Transaktionsmodus für die meisten relationalen Datenbanken.  
  
 Transaktionen in ODBC müssen nicht explizit initiiert werden. Stattdessen beginnt eine Transaktion implizit, wenn die Anwendung mit dem Betrieb in der Datenbank beginnt. Wenn die Datenquelle eine explizite Transaktions Initiierung erfordert, muss Sie vom Treiber bereitgestellt werden, wenn die Anwendung eine Anweisung ausführt, die eine Transaktion erfordert und keine aktuelle Transaktion vorhanden ist.
