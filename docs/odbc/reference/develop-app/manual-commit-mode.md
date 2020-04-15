---
title: Manueller Commit-Modus | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287874"
---
# <a name="manual-commit-mode"></a>Manualcommitmodus
*Im manuellen Commit-Modus* müssen Anwendungen Transaktionen explizit abschließen, indem sie **SQLEndTran** aufrufen, um sie zu übertragen oder zurückzusetzen. Dies ist der normale Transaktionsmodus für die meisten relationalen Datenbanken.  
  
 Transaktionen in ODBC müssen nicht explizit initiiert werden. Stattdessen wird eine Transaktion implizit gestartet, wenn die Anwendung mit der Arbeit in der Datenbank beginnt. Wenn die Datenquelle eine explizite Transaktionsinitiierung erfordert, muss der Treiber sie immer dann bereitstellen, wenn die Anwendung eine Anweisung ausführt, die eine Transaktion erfordert, und es keine aktuelle Transaktion gibt.
