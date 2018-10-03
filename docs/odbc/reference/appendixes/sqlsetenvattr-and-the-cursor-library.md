---
title: SQLSetEnvAttr und die Cursorbibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74e57f98b7d5e3e1508a960b342521ea5d315a3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47693488"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr und die Cursorbibliothek
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetEnvAttr** -Funktion mit der Cursorbibliothek. Allgemeine Informationen zur **SQLSetEnvAttr**, finden Sie unter [SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Die Cursorbibliothek ist die Einstellung des Attributs Umgebung SQL_ATTR_ODBC_VERSION, unabhängig von der Version der Anwendung oder Treiberversion betroffen.
