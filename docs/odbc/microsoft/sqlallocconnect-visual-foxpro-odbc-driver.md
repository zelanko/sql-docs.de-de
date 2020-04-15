---
title: SQLAllocConnect (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e5fa95bb958431f717c073673e0b4ad93056e62
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300664"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Ordnet Speicher für ein Verbindungshandle *hdbc*in der von *henv*identifizierten Umgebung zu. Der Treiber-Manager verarbeitet diesen Aufruf und ruft **SQLAllocConnect** des Treibers auf, wenn [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**oder [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) aufgerufen wird.  
  
 Weitere Informationen finden Sie unter [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) in der *ODBC-Programmiererreferenz*.
