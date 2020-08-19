---
description: Gebundene Deskriptordatensätze
title: Datensätze gebundener Deskriptoren | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcf88374967b5a9d8426d16c9e92c06e4eef32cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476802"
---
# <a name="bound-descriptor-records"></a>Gebundene Deskriptordatensätze
Wenn die Anwendung das SQL_DESC_DATA_PTR-Feld eines deskriptordaten Satzes festlegt, sodass Sie keinen NULL-Wert mehr enthält, wird der Datensatz als *gebunden*bezeichnet.  
  
 Wenn der Deskriptor ein APD ist, stellt jeder gebundene Datensatz einen gebundenen Parameter dar. Bei Eingabe Parametern muss die Anwendung einen Parameter für jede dynamische Parameter Markierung in der SQL-Anweisung binden, bevor die Anweisung ausgeführt wird. Bei Ausgabeparametern muss der Parameter von der Anwendung nicht gebunden werden.  
  
 Wenn es sich bei dem Deskriptor um eine ARD handelt, die eine Zeile mit Datenbankdaten beschreibt, stellt jeder gebundene Datensatz eine gebundene Spalte dar.
