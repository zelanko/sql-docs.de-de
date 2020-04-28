---
title: Schreib geschützter Status (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb585d4712b6cac5e09b65ee8e13604763cd0164
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304021"
---
# <a name="read-only-status-excel-driver"></a>Status „Schreibgeschützt“ (Excel-Treiber)
Wenn der Microsoft Excel-Treiber verwendet wird, werden Datenquellen Tabellen standardmäßig als schreibgeschützt geöffnet und können jeweils nur von einem Benutzer geöffnet werden. Obwohl Tabellen den schreibgeschützten Status aufweisen, können Anwendungen jedoch Insertionen und Updates für Microsoft Excel-Tabellen ausführen.  
  
 Wenn eine Anwendung über den Microsoft Excel-Treiber einen Befehl "Speichern unter" für Microsoft Excel-Daten ausführt, sollte die Anwendung eine neue Tabelle erstellen und die Daten einfügen, die in der neuen Tabelle gespeichert werden sollen. Einfügungen führen zu einem Anfüge Ende an die Tabelle. Es können keine anderen Vorgänge für die Tabelle ausgeführt werden, bis Sie geschlossen und erneut geöffnet wird. Nachdem die Tabelle geschlossen wurde, kann keine nachfolgende Einfügung ausgeführt werden, da es sich bei der Tabelle um eine schreibgeschützte Tabelle handelt.  
  
 Es ist möglich, Werte bei Verwendung des Microsoft Excel-Treibers zu aktualisieren, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert, sodass Updates nicht als offiziell vom Microsoft Excel-Treiber unterstützt werden.
