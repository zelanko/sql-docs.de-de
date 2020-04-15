---
title: SQLGetData- und Blockcursor | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299750"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** arbeitet für eine einzelne Spalte einer einzelnen Zeile und kann kein Array abrufen, das Daten aus mehreren Zeilen enthält. Dies liegt daran, dass **sqlGetData** in erster Linie zum Abrufen langer Daten in Teilen verwendet wird, und es gibt wenig oder keinen Grund, dies für mehr als eine Zeile gleichzeitig zu tun.  
  
 Um **SQLGetData** mit einem Blockcursor zu verwenden, ruft eine Anwendung **SQLSetPos** zuerst auf, um den Cursor in einer einzelnen Zeile zu positionieren. Anschließend wird **SQLGetData** für eine Spalte in dieser Zeile auf. Dieses Verhalten ist jedoch optional. Um zu ermitteln, ob ein Treiber die Verwendung von **SQLGetData** mit Blockcursorn unterstützt, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS auf.
