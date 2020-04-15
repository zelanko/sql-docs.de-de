---
title: Gebundene Deskriptor-Datensätze | Microsoft Docs
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
ms.openlocfilehash: 155ef4951abddc7a73d9d4abfbc45248f33d653c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306307"
---
# <a name="bound-descriptor-records"></a>Gebundene Deskriptordatensätze
Wenn die Anwendung das SQL_DESC_DATA_PTR Feld eines Deskriptordatensatzes so festlegt, dass er keinen Nullwert mehr enthält, wird der Datensatz als *gebunden bezeichnet.*  
  
 Wenn der Deskriptor eine APD ist, stellt jeder gebundene Datensatz einen gebundenen Parameter dar. Bei Eingabeparametern muss die Anwendung einen Parameter für jede dynamische Parametermarkierung in der SQL-Anweisung binden, bevor die Anweisung ausgeführt wird. Für Ausgabeparameter muss die Anwendung den Parameter nicht binden.  
  
 Wenn es sich bei dem Deskriptor um eine ARD handelt, die eine Zeile von Datenbankdaten beschreibt, stellt jeder gebundene Datensatz eine gebundene Spalte dar.
