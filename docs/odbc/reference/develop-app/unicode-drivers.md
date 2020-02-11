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
ms.openlocfilehash: ca9b70ee6a96759e496b831f7c12dc3ee78419b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087870"
---
# <a name="unicode-drivers"></a>Unicode-Treiber
Ob ein Treiber ein Unicode-Treiber oder ein ANSI-Treiber ist, hängt vollständig von der Art der Datenquelle ab. Wenn die Datenquelle Unicode-Daten unterstützt, sollte es sich bei dem Treiber um einen Unicode-Treiber handeln. Wenn die Datenquelle nur ANSI-Daten unterstützt, sollte der Treiber ein ANSI-Treiber bleiben.  
  
 Ein Unicode-Treiber muss **sqlconnectw** exportieren, um vom Treiber-Manager als Unicode-Treiber erkannt zu werden.  
  
 Ein Unicode-Treiber muss Unicode-Funktionen (mit dem Suffix *W*) akzeptieren und Unicode-Daten speichern. Sie kann auch ANSI-Funktionen akzeptieren, ist aber für nicht erforderlich. (Der Treiber-Manager übergibt keinen ANSI-Funktions Aufrufer mit dem Suffix " *A* " an den Treiber, konvertiert ihn aber in einen ANSI-Funktions Aufrufer ohne das-Suffix und übergibt ihn an den Treiber.)  
  
 Abhängig von der Bindung der Anwendung muss ein Unicode-Treiber in der Lage sein, Resultsets entweder in Unicode oder ANSI zurückzugeben. Wenn eine Anwendung an SQL_C_CHAR gebunden wird, muss der Unicode-Treiber SQL_WCHAR Daten in SQL_CHAR konvertieren. Der Treiber-Manager ordnet SQL_C_WCHAR SQL_C_CHAR für ANSI-Treiber zu, ohne dass Unicode-Treiber zugeordnet werden.  
  
> [!NOTE]  
>  Wenn Sie den Treibertyp ermitteln, ruft der Treiber-Manager **SQLSetConnectAttr** auf und legt das SQL_ATTR_ANSI_APP-Attribut zur Verbindungszeit fest. Wenn die Anwendung ANSI-APIs verwendet, wird SQL_ATTR_ANSI_APP auf SQL_AA_TRUE festgelegt, und wenn Unicode verwendet wird, wird Sie auf den Wert SQL_AA_FALSE festgelegt. Dieses Attribut wird verwendet, damit der Treiber basierend auf dem Anwendungstyp ein anderes Verhalten aufweisen kann. Das Attribut kann nicht direkt von der Anwendung festgelegt werden, und es wird nicht von **SQLGetConnectAttr**unterstützt. Wenn ein Treiber für ANSI-und Unicode-Anwendungen dasselbe Verhalten aufweist, sollte er SQL_ERROR für dieses Attribut zurückgeben. Wenn der Treiber SQL_SUCCESS zurückgibt, werden die ANSI-und Unicode-Verbindungen vom Treiber-Manager getrennt, wenn Verbindungs Pooling verwendet wird.
