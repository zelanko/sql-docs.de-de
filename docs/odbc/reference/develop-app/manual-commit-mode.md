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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a00ff373e374d0940b3e7259eeb01e26b620cae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287874"
---
# <a name="manual-commit-mode"></a>Manualcommitmodus
*Im manuellen Commitmodus* müssen Anwendungen die Transaktionen explizit vervollständigen, indem Sie **SQLEndTran** aufrufen, um Sie zu committen oder einen Rollback auszuführen. Dies ist der normale Transaktionsmodus für die meisten relationalen Datenbanken.  
  
 Transaktionen in ODBC müssen nicht explizit initiiert werden. Stattdessen beginnt eine Transaktion implizit, wenn die Anwendung mit dem Betrieb in der Datenbank beginnt. Wenn die Datenquelle eine explizite Transaktions Initiierung erfordert, muss Sie vom Treiber bereitgestellt werden, wenn die Anwendung eine Anweisung ausführt, die eine Transaktion erfordert und keine aktuelle Transaktion vorhanden ist.
