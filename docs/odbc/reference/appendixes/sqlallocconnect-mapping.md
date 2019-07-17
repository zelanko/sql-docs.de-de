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
ms.openlocfilehash: 65c23f41ea9176c460c8fb32ece5e74dfb803541
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065023"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect-Zuordnung
Wenn eine Anwendung ruft **SQLAllocConnect** über einen ODBC 3.. *X* Treiber, den Aufruf von **SQLAllocConnect**(*Henv*, *Phdbc*) zugeordnet ist **SQLAllocHandle** wie folgt:  
  
1.  Der Treiber-Manager weist eine Verbindung und gibt sie an die Anwendung zurück.  
  
2.  Wenn die Anwendung eine Verbindung hergestellt wird, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     in den Treiber mit *InputHandle* festgelegt *Henv*, und *OutputHandlePtr* festgelegt *Phdbc*.
