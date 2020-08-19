---
description: SQLGetData und Blockcursor
title: SQLGetData und Blockcursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f53358b2d4d8dfef1a5a820ed3943f07a584a595
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424492"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** funktioniert für eine einzelne Spalte einer einzelnen Zeile und kann kein Array mit Daten aus mehreren Zeilen abrufen. Dies liegt daran, dass die primäre Verwendung von **SQLGetData** das Abrufen von Long-Daten in Teilen ist, und es gibt nur wenig oder keinen Grund, dies für mehr als eine Zeile gleichzeitig zu erledigen.  
  
 Um **SQLGetData** mit einem Block Cursor zu verwenden, ruft eine Anwendung zuerst **SQLSetPos** auf, um den Cursor in einer einzelnen Zeile zu positionieren. Anschließend wird **SQLGetData** für eine Spalte in dieser Zeile aufgerufen. Dieses Verhalten ist jedoch optional. Um festzustellen, ob ein Treiber die Verwendung von **SQLGetData** mit Block Cursorn unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_GETDATA_EXTENSIONS-Option auf.
