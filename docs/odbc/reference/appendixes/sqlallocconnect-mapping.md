---
title: Sqlordcconnect-Zuordnung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65c23f41ea9176c460c8fb32ece5e74dfb803541
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065023"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect-Zuordnung
Wenn eine Anwendung **sqlzucconnect** über einen ODBC 3 aufruft. *x* -Treiber: der Befehl **sqlzuordcconnect**(*HENV*, *phdbc*) wird **sqlzuzuordchandle** wie folgt zugeordnet:  
  
1.  Der Treiber-Manager weist eine Verbindung zu und gibt Sie an die Anwendung zurück.  
  
2.  Wenn die Anwendung eine Verbindung herstellt, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     im Treiber, bei dem *InputHandle* auf *HENV*festgelegt ist und *outputhandleptr* auf *phdbc*festgelegt ist.
