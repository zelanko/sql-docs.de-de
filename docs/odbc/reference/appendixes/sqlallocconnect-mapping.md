---
title: SQLAllocConnect-Zuordnung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25e72cd3830cea8504983f4348f6c200261490f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305521"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect-Zuordnung
Wenn eine Anwendung **SQLAllocConnect** über einen ODBC 3 aufruft. *x-Treiber* wird der Aufruf von **SQLAllocConnect**(*henv*, *phdbc*) **SQLAllocHandle** wie folgt zugeordnet:  
  
1.  Der Treiber-Manager weist eine Verbindung zu und gibt sie an die Anwendung zurück.  
  
2.  Wenn die Anwendung eine Verbindung herstellt, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     im Treiber mit *InputHandle* auf *henv*gesetzt und *OutputHandlePtr* auf *phdbc*gesetzt.
