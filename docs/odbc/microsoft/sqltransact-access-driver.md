---
title: SQLTransact (Zugriffstreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f88d3154925ab589a8519cb9205da03e8c3dc08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299263"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden SQL_COMMIT und SQL_ROLLBACK für das *fType-Argument* in einem Aufruf von **SQLTransact**unterstützt.  
  
 Wenn während des Commit-Vorgangs ein Fehler auftritt, kann die betroffene Datenbank mithilfe der Option Datenbank reparieren im Microsoft Access-Treibersetup oder durch die Verwendung des Schlüsselworts REPAIR_DB in der **SQLConfigDataSource-Funktion** repariert werden.
