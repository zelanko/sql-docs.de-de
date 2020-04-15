---
title: Deskriptorübergänge | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec5c26bdde8a0d470f2d93e753504bf1c51edcc0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307041"
---
# <a name="descriptor-transitions"></a>Deskriptorübergänge
ODBC-Deskriptoren haben die folgenden drei Zustände.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|D0|Nicht zugewiesener Deskriptor|  
|D1i|Implizit zugewiesener Deskriptor|  
|D1e|Explizit zugewiesener Deskriptor|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Deskriptorstatus auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e[2]|--|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH) [2]|(HY017)|D0|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(IH) [1]|--|--|  
  
 [1] Diese Zeile zeigt Übergänge, wenn *DescriptorHandle* das Handle einer ARD, APD oder IPD war, oder (für **SQLSetDescField**), wenn *DescriptorHandle* das Handle eines IRD war und *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR war.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--|--|--|
