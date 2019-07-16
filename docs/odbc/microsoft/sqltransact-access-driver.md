---
title: SQLTransact (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f4d4b3d8d417591bd72dde22240c81a91d80f990
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948970"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn die Microsoft Access-Treiber verwendet wird, die sql_commit-Option und SQL_ROLLBACK werden für unterstützt die *fType* Argument in einem Aufruf von **SQLTransact**.  
  
 Wenn ein Fehler bei der Commit auftritt, die betroffene Datenbank kann behoben werden, verwenden die Option Reparieren der Datenbank in der Microsoft Access-Treiber-Installation durchführen oder das REPAIR_DB-Schlüsselwort in der **SQLConfigDataSource** -Funktion.
