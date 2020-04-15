---
title: Schreibgeschützter Status (Excel-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304021"
---
# <a name="read-only-status-excel-driver"></a>Status „Schreibgeschützt“ (Excel-Treiber)
Wenn der Microsoft Excel-Treiber verwendet wird, werden Datenquellentabellen standardmäßig schreibgeschützt geöffnet und können jeweils nur von einem Benutzer geöffnet werden. Obwohl Tabellen den schreibgeschützten Status haben, können Anwendungen Einfügungen und Aktualisierungen für Microsoft Excel-Tabellen durchführen.  
  
 Wenn eine Anwendung über den Microsoft Excel-Treiber einen Befehl Speichern unter für Microsoft Excel-Daten ausführt, sollte die Anwendung eine neue Tabelle erstellen und die zu speichernden Daten in die neue Tabelle einfügen. Einfügungen ergeben ein Anfügen an die Tabelle. Es können keine anderen Vorgänge für die Tabelle ausgeführt werden, bis sie geschlossen und erneut geöffnet wird. Nach dem Schließen der Tabelle kann keine nachträgliche Einfügung ausgeführt werden, da es sich bei der Tabelle um eine schreibgeschützte Tabelle handelt.  
  
 Es ist möglich, Werte zu aktualisieren, wenn Sie den Microsoft Excel-Treiber verwenden, aber eine Zeile kann nicht aus einer Tabelle gelöscht werden, die auf einer Microsoft Excel-Tabelle basiert, sodass Updates nicht offiziell vom Microsoft Excel-Treiber unterstützt werden.
