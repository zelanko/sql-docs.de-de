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
ms.openlocfilehash: 4d0016a2849feb5656cb3cd6dd46eff444f37058
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118760"
---
# <a name="bound-descriptor-records"></a>Gebundene Deskriptordatensätze
Wenn die Anwendung das SQL_DESC_DATA_PTR-Feld von einem anwendungsparameterdeskriptor-Datensatz wird, sodass sie nicht mehr auf einen null-Wert enthält, der Datensatz gilt als *gebunden*.  
  
 Wenn der Deskriptor einer APD ist, stellt jeder gebundene Datensatz einen gebundenen Parameter dar. Bei Eingabeparametern muss die Anwendung einen Parameter für jeden Marker dynamischer Parameter in der SQL-Anweisung vor der Ausführung der Anweisung binden. Für Ausgabeparameter muss die Anwendung der Parameter nicht gebunden.  
  
 Ist der Deskriptor einer ARD, die eine Zeile mit Datenbankdaten beschreibt, stellt jeder gebundene Datensatz eine gebundene Spalte dar.
