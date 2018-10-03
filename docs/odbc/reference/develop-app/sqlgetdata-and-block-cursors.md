---
title: SQLGetData und Blockcursor | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: a14c98f045fd974b404209cc998496dc5fa7193e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755524"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** greift auf eine einzelne Spalte aus einer einzelnen Zeile und ein Array mit Daten aus mehreren Zeilen kann nicht abgerufen werden. Dies ist, da die primäre Verwendung von **SQLGetData** wird zum Abrufen von long-Daten in Teilen, und es ist wenig oder keinen Grund dafür für mehr als eine Zeile zu einem Zeitpunkt.  
  
 Verwendung von **SQLGetData** mit einem Blockcursor, ruft eine Anwendung zuerst **SQLSetPos** zur Positionierung des Cursors für eine einzelne Zeile. Es ruft dann **SQLGetData** für eine Spalte in dieser Zeile. Dieses Verhalten ist jedoch optional. Um festzustellen, ob ein Treiber die Verwendung eines unterstützt **SQLGetData** mit Blockcursorn, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS.
