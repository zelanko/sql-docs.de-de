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
ms.openlocfilehash: db1608415ae74bcaafd89f4afe01393cfb700379
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125556"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr und die Cursorbibliothek
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetEnvAttr** -Funktion mit der Cursorbibliothek. Allgemeine Informationen zur **SQLSetEnvAttr**, finden Sie unter [SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Die Cursorbibliothek ist die Einstellung des Attributs Umgebung SQL_ATTR_ODBC_VERSION, unabhängig von der Version der Anwendung oder Treiberversion betroffen.
