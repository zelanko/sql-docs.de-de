---
title: Mehrere hstmts (Paradox-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5e7a9a4ec0d6426779fb55d923bc7f0607089aad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68045028"
---
# <a name="multiple-hstmts-paradox-driver"></a>Mehrere hstmts (Paradox-Treiber)
Wenn Sie den ODBC-Paradox-Treiber verwenden, wenn Sie mehr als ein *hstmt* zum Ausführen von Abfragen für eine Tabelle verwenden möchten, muss die Tabelle über einen eindeutigen Index verfügen (Paradox-Primärschlüssel).
