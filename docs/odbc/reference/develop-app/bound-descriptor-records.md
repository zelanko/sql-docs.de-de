---
title: Gebundene Deskriptordatensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f7d21a1166868603f9389ab4ef5c5b3448b0312
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199530"
---
# <a name="bound-descriptor-records"></a>Gebundene Deskriptordatensätze
Wenn die Anwendung das SQL_DESC_DATA_PTR-Feld von einem anwendungsparameterdeskriptor-Datensatz wird, sodass sie nicht mehr auf einen null-Wert enthält, der Datensatz gilt als *gebunden*.  
  
 Wenn der Deskriptor einer APD ist, stellt jeder gebundene Datensatz einen gebundenen Parameter dar. Bei Eingabeparametern muss die Anwendung einen Parameter für jeden Marker dynamischer Parameter in der SQL-Anweisung vor der Ausführung der Anweisung binden. Für Ausgabeparameter muss die Anwendung der Parameter nicht gebunden.  
  
 Ist der Deskriptor einer ARD, die eine Zeile mit Datenbankdaten beschreibt, stellt jeder gebundene Datensatz eine gebundene Spalte dar.
