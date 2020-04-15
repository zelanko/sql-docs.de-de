---
title: Dateidatenquellen | Microsoft Docs
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
ms.openlocfilehash: 0661aa424a7a118b8b12f4bf8433987ff83bd788
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306651"
---
# <a name="file-data-sources"></a>Dateidatenquellen
*Dateidatenquellen* werden in einer Datei gespeichert und ermöglichen die wiederholte Verwendung von Verbindungsinformationen durch einen einzelnen Benutzer oder die von mehreren Benutzern gemeinsam genutzt werden. Wenn eine Dateidatenquelle verwendet wird, stellt der Treiber-Manager die Verbindung zur Datenquelle mithilfe der Informationen in einer Dsn-Datei her. Diese Datei kann wie jede andere Datei bearbeitet werden. Eine Dateidatenquelle hat keinen Datenquellennamen, ebenso wie eine Computerdatenquelle, und ist nicht für einen Benutzer oder Computer registriert.  
  
 Eine Dateidatenquelle optimiert den Verbindungsprozess, da die Dsn-Datei die Verbindungszeichenfolge enthält, die andernfalls für einen Aufruf der **SQLDriverConnect-Funktion** erstellt werden müsste. Ein weiterer Vorteil der .dsn-Datei ist, dass sie auf jeden Computer kopiert werden kann, so dass identische Datenquellen von vielen Computern verwendet werden können, solange sie den entsprechenden Treiber installiert haben. Eine Dateidatenquelle kann auch von Anwendungen gemeinsam genutzt werden. Eine gemeinsam genutzte Dateidatenquelle kann in einem Netzwerk platziert und gleichzeitig von mehreren Anwendungen verwendet werden.  
  
 Eine .dsn-Datei kann auch nicht mehr gemeinsam nutzen können. Eine nicht gemeinsam nutzende .dsn-Datei befindet sich auf einem einzelnen Computer und zeigt auf eine Computerdatenquelle. Nicht gemeinsam nutzende Dateidatenquellen existieren hauptsächlich, um die einfache Konvertierung von Maschinendatenquellen in Dateidatenquellen zu ermöglichen, sodass eine Anwendung so konzipiert werden kann, dass sie ausschließlich mit Dateidatenquellen funktioniert. Wenn der Treiber-Manager die Informationen in einer nicht gemeinsam nutzenden Dateidatenquelle sendet, stellt er bei Bedarf eine Verbindung mit der Computerdatenquelle her, auf die die DSN-Datei verweist.  
  
 Weitere Informationen zu Dateidatenquellen finden Sie unter [Verbinden mit Dateidatenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)oder in der [SQLDriverConnect-Funktionsbeschreibung.](../../odbc/reference/syntax/sqldriverconnect-function.md)
