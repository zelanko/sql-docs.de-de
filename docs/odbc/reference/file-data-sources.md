---
description: Dateidatenquellen
title: Datei Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d02c767adab90ee4a7b6ff93a34886c03b87780c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429042"
---
# <a name="file-data-sources"></a>Dateidatenquellen
*Datei Datenquellen* werden in einer Datei gespeichert, sodass Verbindungsinformationen von einem einzelnen Benutzer wiederholt verwendet oder von mehreren Benutzern gemeinsam verwendet werden können. Wenn eine Datei Datenquelle verwendet wird, stellt der Treiber-Manager die Verbindung mit der Datenquelle mithilfe der Informationen in einer DSN-Datei her. Diese Datei kann wie jede andere Datei bearbeitet werden. Eine Datei Datenquelle hat keinen Datenquellen Namen, wie eine Computer Datenquelle, und ist nicht für einen Benutzer oder Computer registriert.  
  
 Eine Datei Datenquelle optimiert den Verbindungsprozess, da die DSN-Datei die Verbindungs Zeichenfolge enthält, die andernfalls für einen aufzurufenden Befehl der **SQLDriverConnect** -Funktion erstellt werden müsste. Ein weiterer Vorteil der DSN-Datei besteht darin, dass Sie auf einen beliebigen Computer kopiert werden kann, sodass identische Datenquellen von vielen Computern verwendet werden können, sofern Sie den entsprechenden Treiber installiert haben. Eine Datei Datenquelle kann auch von Anwendungen gemeinsam genutzt werden. Eine Datenquelle, die für die Datenquelle verwendet werden kann, kann in einem Netzwerk platziert und von mehreren Anwendungen gleichzeitig verwendet werden.  
  
 Eine DSN-Datei kann auch nicht mehr in der Share Bare Datei enthalten sein. Eine nicht Shareable. DSN-Datei befindet sich auf einem einzelnen Computer und verweist auf eine Computer Datenquelle. Nicht gemeinsam verwendbare Datei Datenquellen bestehen hauptsächlich darin, die einfache Konvertierung von Computer Datenquellen in Datei Datenquellen zu ermöglichen, sodass eine Anwendung nur für die Verwendung von Datei Datenquellen entworfen werden kann. Wenn der Treiber-Manager die Informationen in einer nicht Share baren Datei Datenquelle sendet, stellt er bei Bedarf eine Verbindung mit der Computer Datenquelle her, auf die die DSN-Datei verweist.  
  
 Weitere Informationen zu Datei Datenquellen finden Sie unter [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder in der Beschreibung der [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) -Funktion.
