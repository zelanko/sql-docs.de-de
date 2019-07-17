---
title: Der Deskriptor Übergänge | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44e9d92c7371451d6bfdd2e1513c3f8fdac8447b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129998"
---
# <a name="descriptor-transitions"></a>Deskriptorübergänge
ODBC-Deskriptoren müssen die folgenden drei Zustände.  
  
|Status|Beschreibung|  
|-----------|-----------------|  
|D0|Nicht zugeordnete Sicherheitsbeschreibung|  
|D1i|Implizit zugewiesene Deskriptor|  
|D1e|Explizit zugewiesene Deskriptor|  
  
 Die folgenden Tabellen zeigen, wie jede ODBC-Funktion den Zustand der Deskriptor auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e [2]|--|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(BEI) [2]|(HY017)|D0|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|(BEI) [1]|--|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *DescriptorHandle* wurde das Handle eines ARD, APD oder IPD, oder (für **SQLSetDescField**) beim *DescriptorHandle* wurde das Handle für ein IRD und *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR war.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implizit|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--|--|--|
