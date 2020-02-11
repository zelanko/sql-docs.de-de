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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4841d8d923ff73d187569df3d7f9e29daf0f4e48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107399"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** funktioniert für eine einzelne Spalte einer einzelnen Zeile und kann kein Array mit Daten aus mehreren Zeilen abrufen. Dies liegt daran, dass die primäre Verwendung von **SQLGetData** das Abrufen von Long-Daten in Teilen ist, und es gibt nur wenig oder keinen Grund, dies für mehr als eine Zeile gleichzeitig zu erledigen.  
  
 Um **SQLGetData** mit einem Block Cursor zu verwenden, ruft eine Anwendung zuerst **SQLSetPos** auf, um den Cursor in einer einzelnen Zeile zu positionieren. Anschließend wird **SQLGetData** für eine Spalte in dieser Zeile aufgerufen. Dieses Verhalten ist jedoch optional. Um festzustellen, ob ein Treiber die Verwendung von **SQLGetData** mit Block Cursorn unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_GETDATA_EXTENSIONS-Option auf.
