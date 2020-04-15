---
title: Deskriptoren | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305901"
---
# <a name="descriptors"></a>Deskriptoren
Ein Deskriptorhandle bezieht sich auf eine Datenstruktur, die Informationen über Spalten oder dynamische Parameter enthält.  
  
 ODBC-Funktionen, die auf Spalten- und Parameterdaten arbeiten, legen implizit Deskriptorfelder fest und rufen sie ab. Wenn **sqlBindCol** beispielsweise aufgerufen wird, Spaltendaten zu binden, werden Deskriptorfelder festgelegt, die die Bindung vollständig beschreiben. Wenn **SQLColAttribute** aufgerufen wird, um Spaltendaten zu beschreiben, werden in Deskriptorfeldern gespeicherte Daten zurückgegeben.  
  
 Eine Anwendung, die ODBC-Funktionen aufruft, muss sich nicht mit Deskriptoren befassen. Kein Datenbankvorgang erfordert, dass die Anwendung direkten Zugriff auf Deskriptoren erhält. Bei einigen Anwendungen optimiert der direkte Zugriff auf Deskriptoren jedoch viele Vorgänge. Der direkte Zugriff auf Deskriptoren bietet beispielsweise eine Möglichkeit, Spaltendaten neu zu binden, was effizienter sein kann, als **SQLBindCol** erneut aufzurufen.  
  
> [!NOTE]  
>  Die physische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten direkten Zugriff auf einen Deskriptor nur, indem sie seine Felder bearbeiten, indem sie ODBC-Funktionen mit dem Deskriptor-Handle aufrufen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Typen von Deskriptoren](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Zuordnen und Freigeben von Deskriptoren](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Abrufen und Festlegen von Deskriptorfeldern](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
