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
ms.openlocfilehash: 4841d8d923ff73d187569df3d7f9e29daf0f4e48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107399"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData und Blockcursor
**SQLGetData** greift auf eine einzelne Spalte aus einer einzelnen Zeile und ein Array mit Daten aus mehreren Zeilen kann nicht abgerufen werden. Dies ist, da die primäre Verwendung von **SQLGetData** wird zum Abrufen von long-Daten in Teilen, und es ist wenig oder keinen Grund dafür für mehr als eine Zeile zu einem Zeitpunkt.  
  
 Verwendung von **SQLGetData** mit einem Blockcursor, ruft eine Anwendung zuerst **SQLSetPos** zur Positionierung des Cursors für eine einzelne Zeile. Es ruft dann **SQLGetData** für eine Spalte in dieser Zeile. Dieses Verhalten ist jedoch optional. Um festzustellen, ob ein Treiber die Verwendung eines unterstützt **SQLGetData** mit Blockcursorn, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_GETDATA_EXTENSIONS.
