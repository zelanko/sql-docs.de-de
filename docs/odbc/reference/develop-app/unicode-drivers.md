---
title: Unicode-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e555ff4a3b33c4c827371dc1ad63546736d7189
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745858"
---
# <a name="unicode-drivers"></a>Unicode-Treiber
Ob ein Treiber einen Unicode-Treiber oder ein Treiber ANSI sein soll, hängt ganz von der Art der Datenquelle. Wenn die Datenquelle Unicode-Daten unterstützt, muss der Treiber einen Unicode-Treiber. Wenn die Datenquelle nur ANSI-Daten unterstützt, sollte der Treiber ein ANSI-Treiber bleiben.  
  
 Ein Unicode-Treiber muss exportieren **SQLConnectW** als Unicode-Treiber vom Treiber-Manager erkannt werden.  
  
 Ein Unicode-Treiber muss Unicode-Funktionen akzeptieren (mit dem Suffix *W*) und Unicode-Daten zu speichern. Es kann auch ANSI-Funktionen annehmen, aber es ist nicht erforderlich, um. (Der Treiber-Manager übergibt die nicht den Aufruf einer ANSI-Funktion mit dem *ein* suffix jedoch mit dem Treiber, konvertiert es in das ANSI-Funktionsaufruf ohne das Suffix und übergibt dann diese an den Treiber.)  
  
 Ein Unicode-Treiber muss Resultsets in Unicode oder ANSI, abhängig von der Anwendung Bindung zurückgeben können. Wenn eine Anwendung an SQL_C_CHAR gebunden werden soll, muss der Unicode-Treiber SQL_WCHAR-Daten in SQL_CHAR konvertieren. Der Treiber-Manager ordnen SQL_C_WCHAR SQL_C_CHAR für ANSI-Treiber, aber es ist keine Zuordnung für Unicode-Treiber.  
  
> [!NOTE]  
>  Wenn Sie den Treibertyp zu bestimmen, ruft der Treiber-Manager **SQLSetConnectAttr** und legen Sie das Attribut SQL_ATTR_ANSI_APP zur Verbindungszeit erfolgt ist. Wenn die Anwendung die ANSI-APIs verwendet wird, wird SQL_ATTR_ANSI_APP auf SQL_AA_TRUE festgelegt, und wenn Unicode verwendet wird, wird er auf einen Wert von SQL_AA_FALSE festgelegt sein. Dieses Attribut wird verwendet, sodass der Treiber anderes Verhalten basierend auf den Anwendungstyp aufweisen kann. Das Attribut kann nicht direkt von der Anwendung festgelegt werden, und es wird nicht von **SQLGetConnectAttr**. Wenn ein Treiber für ANSI- und Unicode-Anwendungen das gleiche Verhalten aufweist, muss er SQL_ERROR für dieses Attribut zurückgeben. Wenn der Treiber SQL_SUCCESS zurückgegeben wird, wird der Treiber-Manager ANSI- und Unicode-Verbindungen trennen, wenn Verbindungspooling verwendet wird.
