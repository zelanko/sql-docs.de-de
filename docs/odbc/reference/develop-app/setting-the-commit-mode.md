---
title: Festlegen des Commitmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a43a78ad9453f65d9b12595851bd622f720b409a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094221"
---
# <a name="setting-the-commit-mode"></a>Festlegen des Commitmodus
Anwendungen Geben Sie den Transaktionsmodus mit das SQL_ATTR_AUTOCOMMIT-Verbindungsattribut. ODBC-Transaktionen werden standardmäßig im Autocommit Modus (es sei denn, **SQLSetConnectAttr** und **SQLSetConnectOption** werden nicht unterstützt, dies ist wahrscheinlich nicht). Der Wechsel von Manualcommit-Modus in den Autocommit-Modus automatisch führt einen Commit alle geöffneten Transaktionen für die Verbindung aus.
