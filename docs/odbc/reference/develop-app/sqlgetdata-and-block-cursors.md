---
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
ms.openlocfilehash: b60d7093552b8f1dbed87d9ad8840ddb5a9e0799
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299750"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** funktioniert für eine einzelne Spalte einer einzelnen Zeile und kann kein Array mit Daten aus mehreren Zeilen abrufen. Dies liegt daran, dass die primäre Verwendung von **SQLGetData** das Abrufen von Long-Daten in Teilen ist, und es gibt nur wenig oder keinen Grund, dies für mehr als eine Zeile gleichzeitig zu erledigen.  
  
 Um **SQLGetData** mit einem Block Cursor zu verwenden, ruft eine Anwendung zuerst **SQLSetPos** auf, um den Cursor in einer einzelnen Zeile zu positionieren. Anschließend wird **SQLGetData** für eine Spalte in dieser Zeile aufgerufen. Dieses Verhalten ist jedoch optional. Um festzustellen, ob ein Treiber die Verwendung von **SQLGetData** mit Block Cursorn unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_GETDATA_EXTENSIONS-Option auf.
