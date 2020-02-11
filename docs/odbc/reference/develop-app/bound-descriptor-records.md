---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d0016a2849feb5656cb3cd6dd46eff444f37058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118760"
---
# <a name="bound-descriptor-records"></a>Gebundene Deskriptordatensätze
Wenn die Anwendung das SQL_DESC_DATA_PTR-Feld eines deskriptordaten Satzes festlegt, sodass Sie keinen NULL-Wert mehr enthält, wird der Datensatz als *gebunden*bezeichnet.  
  
 Wenn der Deskriptor ein APD ist, stellt jeder gebundene Datensatz einen gebundenen Parameter dar. Bei Eingabe Parametern muss die Anwendung einen Parameter für jede dynamische Parameter Markierung in der SQL-Anweisung binden, bevor die Anweisung ausgeführt wird. Bei Ausgabeparametern muss der Parameter von der Anwendung nicht gebunden werden.  
  
 Wenn es sich bei dem Deskriptor um eine ARD handelt, die eine Zeile mit Datenbankdaten beschreibt, stellt jeder gebundene Datensatz eine gebundene Spalte dar.
