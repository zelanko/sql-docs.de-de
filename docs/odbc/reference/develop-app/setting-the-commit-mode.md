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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094221"
---
# <a name="setting-the-commit-mode"></a>Festlegen des Commitmodus
Anwendungen geben den Transaktionsmodus mit dem SQL_ATTR_AUTOCOMMIT Verbindungs Attribut an. Standardmäßig befinden sich ODBC-Transaktionen im Autocommit-Modus (es sei denn, **SQLSetConnectAttr** und **SQLSetConnectOption** werden nicht unterstützt, was unwahrscheinlich ist). Wenn Sie vom manuellen Commitmodus in den Autocommit-Modus wechseln, wird für alle geöffneten Transaktionen der Verbindung automatisch ein Commit ausgeführt.
