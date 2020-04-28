---
title: Sqlzugecenv-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb26e3443fabda2d6490c071b1f2668895e66b8d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304041"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv-Zuordnung
Wenn eine Anwendung **sqlzuordcenv** über einen ODBC *3. x* -Treiber aufruft, wird der Aufruf von **sqlzuzuordcenv**(*phenv*) **sqlzuzuordchandle** wie folgt zugeordnet:  
  
1.  Der Treiber-Manager ordnet ein Umgebungs Handle zu und gibt es an die Anwendung zurück. Der Treiber-Manager ruft **SQLSetEnvAttr** auf, um das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC2 festzulegen.  
  
2.  Wenn die Anwendung die erste Verbindung mit einem Treiber herstellt, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     im Treiber, bei dem *outputhandleptr* auf " *phenv*" festgelegt ist.
