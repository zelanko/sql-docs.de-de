---
title: Schreibgeschützten Status (Excel-Treiber) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988044"
---
# <a name="read-only-status-excel-driver"></a>Status „Schreibgeschützt“ (Excel-Treiber)
Wenn der Microsoft Excel-Treiber verwendet wird, wird Datenquellentabellen werden standardmäßig als schreibgeschützt geöffnet, und können jeweils nur ein einziger Benutzer geöffnet werden. Auch wenn Tabellen schreibgeschützten Status aufweisen, können jedoch Anwendungen einfügungen und Updates für Microsoft Excel-Tabellen ausführen.  
  
 Wenn eine Anwendung einen Befehl Speichern unter Microsoft Excel-Daten mithilfe der Microsoft Excel-Treiber durchführt, sollte die Anwendung eine neue Tabelle erstellen und fügen Sie die Daten in die neue Tabelle gespeichert werden soll. Fügt einen Anfügevorgang auf die Tabelle führen. Für die Tabelle können keine anderen Vorgänge ausgeführt werden, bis es geschlossen und erneut geöffnet wird. Nachdem die Tabelle geschlossen wurde, kann keine nachfolgenden einfügungen ausgeführt werden, da die Tabelle klicken Sie dann eine Tabelle schreibgeschützt ist.  
  
 Es ist möglich, Werte zu aktualisieren, wenn der Microsoft Excel-Treiber verwendet, aber eine Zeile kann nicht gelöscht werden, aus einer Tabelle anhand von Microsoft Excel-Arbeitsblatt, damit die Updates nicht berücksichtigt werden offiziell von Microsoft Excel-Treiber unterstützt.
