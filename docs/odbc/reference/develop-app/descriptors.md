---
title: Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2138a5f8417fc9156c916719e96d707b9a29de9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68040007"
---
# <a name="descriptors"></a>Deskriptoren
Ein Deskriptorhandle bezieht sich auf eine Datenstruktur, die Informationen zu Spalten oder dynamische Parameter enthält.  
  
 ODBC-Funktionen, die implizit auf Spalten- und Daten zu arbeiten, festlegen und Abrufen von deskriptorfelder. Z. B. wenn **SQLBindCol** wird aufgerufen, um Spaltendaten zu binden, wird deskriptorfelder, die die Bindung vollständig zu beschreiben. Wenn **SQLColAttribute** wird aufgerufen, um Spaltendaten zu beschreiben, gibt es in deskriptorfeldern gespeicherte Daten.  
  
 Eine Anwendung, die ODBC-Funktionen aufrufen muss mit Deskriptoren nicht darum kümmern. Keine Datenbankvorgang erfordert, dass die Anwendung direkt Deskriptoren zugreifen. Jedoch optimiert die direkten Zugriff auf Deskriptoren viele Vorgänge für einige Anwendungen sind. Beispielsweise leiten den Zugriff auf die Deskriptoren bietet eine Möglichkeit zum Binden von Spaltendaten an, die möglicherweise effizienter als das Aufrufen **SQLBindCol** erneut aus.  
  
> [!NOTE]  
>  Die physikalische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten direkten Zugriff auf den Deskriptor eines nur durch die Felder bearbeiten von Aufrufen von ODBC-Funktionen, mit dem Deskriptorhandle.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Typen von Deskriptoren](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Zuordnen und Freigeben von Deskriptoren](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Abrufen und Festlegen von Deskriptorfeldern](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
