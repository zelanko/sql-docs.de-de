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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca8299daae744fb9398ed6ffc99c838ce8edff48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305901"
---
# <a name="descriptors"></a>Deskriptoren
Ein Deskriptorhandle verweist auf eine Datenstruktur, die Informationen zu Spalten oder dynamischen Parametern enthält.  
  
 ODBC-Funktionen, die auf Spalten-und Parameterdaten angewendet werden, legen Deskriptorfelder implizit fest und rufen diese ab Wenn beispielsweise **SQLBindCol** aufgerufen wird, um Spaltendaten zu binden, werden Deskriptorfelder festgelegt, mit denen die Bindung vollständig beschrieben wird. Wenn **SQLColAttribute** aufgerufen wird, um Spaltendaten zu beschreiben, gibt es die in den Deskriptorfeldern gespeicherten Daten zurück.  
  
 Eine Anwendung, die ODBC-Funktionen aufrufen, muss sich nicht mit Deskriptoren befassen. Kein Daten Bank Vorgang erfordert, dass die Anwendung direkten Zugriff auf Deskriptoren erhält. Bei einigen Anwendungen werden durch das Abrufen des direkten Zugriffs auf Deskriptoren jedoch viele Vorgänge optimiert. Der direkte Zugriff auf Deskriptoren bietet z. b. eine Möglichkeit zum erneuten Binden von Spaltendaten, die effizienter sein können als das erneute Aufrufen von **SQLBindCol** .  
  
> [!NOTE]  
>  Die physische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten nur einen direkten Zugriff auf einen Deskriptor, indem Sie die zugehörigen Felder durch Aufrufen von ODBC-Funktionen mit dem Deskriptorhandle bearbeiten.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Typen von Deskriptoren](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Zuordnen und Freigeben von Deskriptoren](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Abrufen und Festlegen von Deskriptorfeldern](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
