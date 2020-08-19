---
description: Einschränkungen der Verwendung keysetgesteuerter Cursor
title: Einschränkungen bei der Verwendung von keysetgesteuerten Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 611bc032c51760742e5dce4dfbd8e1fa4fe33d0f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483473"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Einschränkungen der Verwendung keysetgesteuerter Cursor
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Sie müssen in der Lage sein, eine einzelne ROWID-Spalte für die abgefragte Tabelle abzurufen. Ein keysetgesteuerte Cursor kann nicht für Joins, Abfragen oder Anweisungen verwendet werden, die unterschiedliche Klauseln, Group by-, Union-, INTERSECT-oder minus-Klauseln enthalten.  
  
 Außerdem funktionieren keysetgesteuerte Cursor nicht, wenn die Anwendung Tabellen Aliase verwendet. vorwärts-oder statische Cursor Typen sind erforderlich. Die Verwendung des Keyset-Cursor Typs mit Tabellenaliasen führt zum folgenden Fehler: "[Microsoft] [ODBC Driver for Oracle] der keysetgesteuerte Cursor kann nicht bei Join, mit Union, INTERSECT oder minus oder im schreibgeschützten Resultset verwendet werden."  
  
> [!NOTE]  
>  Aufgrund der Art und Weise, wie der Treiber die SQL-Anweisung verarbeitet, die an den Oracle-Server gesendet wird, gibt Oracle intern die folgende Fehlermeldung zurück: "Ora-00964: Tabellenname nicht in der Liste."
