---
description: SQLTransact (Access-Treiber)
title: SQLtransact (Zugriffs Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 7e9b00f8f5a12af2d3823171d22ad53106569352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339678"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden SQL_COMMIT und SQL_ROLLBACK für das *ftype* -Argument in einem **SQLTransact**-Befehl unterstützt.  
  
 Wenn während des Commit-Vorgangs ein Fehler auftritt, kann die betroffene Datenbank mithilfe der Option Datenbank reparieren im Setup des Microsoft Access-Treibers oder mithilfe des REPAIR_DB-Schlüssel Worts in der **SQLConfigDataSource** -Funktion repariert werden.
