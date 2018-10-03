---
title: SQLAllocConnect-Zuordnung | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: bdb63e9610d00c0736f640b6f4c4d743f3335c7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606238"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect-Zuordnung
Wenn eine Anwendung ruft **SQLAllocConnect** über einen ODBC 3. *X* Treiber, den Aufruf von **SQLAllocConnect**(*Henv*, *Phdbc*) zugeordnet ist **SQLAllocHandle** wie folgt:  
  
1.  Der Treiber-Manager weist eine Verbindung und gibt sie an die Anwendung zurück.  
  
2.  Wenn die Anwendung eine Verbindung hergestellt wird, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     in den Treiber mit *InputHandle* festgelegt *Henv*, und *OutputHandlePtr* festgelegt *Phdbc*.
