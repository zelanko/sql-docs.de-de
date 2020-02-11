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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 39f9d2e7ba40ba067659a86f45d2006c83594f3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988044"
---
# <a name="read-only-status-excel-driver"></a>Status „Schreibgeschützt“ (Excel-Treiber)
Wenn der Microsoft Excel-Treiber verwendet wird, werden Datenquellen Tabellen standardmäßig als schreibgeschützt geöffnet und können jeweils nur von einem Benutzer geöffnet werden. Obwohl Tabellen den schreibgeschützten Status aufweisen, können Anwendungen jedoch Insertionen und Updates für Microsoft Excel-Tabellen ausführen.  
  
 Wenn eine Anwendung über den Microsoft Excel-Treiber einen Befehl "Speichern unter" für Microsoft Excel-Daten ausführt, sollte die Anwendung eine neue Tabelle erstellen und die Daten einfügen, die in der neuen Tabelle gespeichert werden sollen. Einfügungen führen zu einem Anfüge Ende an die Tabelle. Es können keine anderen Vorgänge für die Tabelle ausgeführt werden, bis Sie geschlossen und erneut geöffnet wird. Nachdem die Tabelle geschlossen wurde, kann keine nachfolgende Einfügung ausgeführt werden, da es sich bei der Tabelle um eine schreibgeschützte Tabelle handelt.  
  
 Es ist möglich, Werte bei Verwendung des Microsoft Excel-Treibers zu aktualisieren, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert, sodass Updates nicht als offiziell vom Microsoft Excel-Treiber unterstützt werden.
